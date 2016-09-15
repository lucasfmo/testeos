---
title: "Przykłady kodu dla systemu Linux | Azure RMS"
description: "W tym temacie przedstawiono ważne scenariusze i elementy kodu dla zestawu SDK usługi RMS w wersji dla systemu Linux."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0F7714CA-1D3E-4846-B187-739825B7DE26
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 11c1598c19392c6ecf0e82817f0ddeecd02c28bf
ms.openlocfilehash: f1c89418cf031eadaf2d65314e1686ae4f00aa8c


---

# Przykłady kodu dla systemu Linux

W tym temacie przedstawiono ważne scenariusze i elementy kodu dla zestawu SDK usługi RMS w wersji dla systemu Linux.

Fragmenty kodu poniżej pochodzą z przykładowych aplikacji, *rms\_sample* i *rmsauth\_sample*. Aby uzyskać więcej informacji, zobacz [przykłady](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples) w repozytorium GitHub.

## Scenariusz: dostęp do informacji o zasadach ochrony z poziomu chronionego pliku

**Otwiera i odczytuje plik chroniony za pomocą usługi RMS**
**Źródło**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Opis**: po otrzymaniu nazwy pliku od użytkownika, odczytaniu certyfikatów (zobacz *MainWindow::addCertificates*), ustawieniu wywołania zwrotnego autoryzacji z identyfikatorem klienta i adresem URL przekierowania, wywołaniu *ConvertFromPFile* (zobacz poniższy przykład kodu) i odczytaniu nazwy zasad ochrony, ich opisu i daty ważności zawartości.

**C++**:

    void MainWindow::ConvertFromPFILE(const string& fileIn,
        const string& clientId,
        const string& redirectUrl,
        const string& clientEmail) 
    {
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    
    if (!inFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    string fileOut;
    
    // generate output filename
    auto pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
     fileOut = fileIn.substr(0, pos);
    }
    
     // create streams
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!outFile->is_open()) {
     AddLog("ERROR: Failed to open ", fileOut.c_str());
     return;
      }
    
    try
    {
    // create authentication context
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    auto pfs = PFileConverter::ConvertFromPFile(
      clientEmail,
      inFile,
      outFile,
      auth,
      this->consent);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e)
    {
    AddLog("ERROR: ", e.error().c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    }
    inFile->close();
    outFile->close();
    }

**Utwórz strumień pliku chronionego**
**Źródło**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Opis**: ta metoda tworzy strumień pliku chronionego z przekazanego zapasowego strumienia poprzez metodę SDK, *ProtectedFileStream::Aquire*, który jest następnie zwracany do obiektu wywołującego.

**C++**:

    shared_ptr<GetProtectedFileStreamResult>PFileConverter::ConvertFromPFile(
    const string           & userId,
    shared_ptr<istream>      inStream,
    shared_ptr<iostream>     outStream,
    IAuthenticationCallback& auth,
    IConsentCallback       & consent)
    {
    auto inIStream = rmscrypto::api::CreateStreamFromStdStream(inStream);
    
    auto fsResult = ProtectedFileStream::Acquire(
    inIStream,
    userId,
    auth,
    consent,
    POL_None,
    static_cast<ResponseCacheFlags>(RESPONSE_CACHE_INMEMORY
                                    | RESPONSE_CACHE_ONDISK));
    
    if ((fsResult.get() != nullptr) && (fsResult->m_status == Success) &&
      (fsResult->m_stream != nullptr)) {
    auto pfs = fsResult->m_stream;
    
    // preparing
    readPosition  = 0;
    writePosition = 0;
    totalSize     = pfs->Size();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    }
      return fsResult;
    }

## Scenariusz: tworzenie nowego pliku chronionego z wykorzystaniem szablonu

**Chroni plik za pomocą szablonu wybranego przez użytkownika**
**Źródło**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Opis**: po otrzymaniu nazwy pliku od użytkownika, odczytaniu certyfikatów (zobacz *MainWindow::addCertificates*) i ustawieniu wywołania zwrotnego autoryzacji z identyfikatorem klienta i adresem URL przekierowania wybrany plik jest chroniony przez wywołanie *ConvertToPFileTemplates* (zobacz poniższy przykład kodu).

**C++**:

    void MainWindow::ConvertToPFILEUsingTemplates(const string& fileIn,
                                              const string& clientId,
                                              const string& redirectUrl,
                                              const string& clientEmail) 
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFileTemplates(
      clientEmail, inFile, fileExt, outFile, auth,
      this->consent, this->templates);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
   catch (const rmsauth::Exception& e) { AddLog("ERROR: ", e.error().c_str()); outFile->close(); remove(fileOut.c_str()); } catch (const rmscore::exceptions::RMSException& e) { AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**Chroni plik za pomocą zasad utworzonych na podstawie szablonu**
**Źródło**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Opis**: lista szablonów skojarzonych z użytkownikiem jest pobierana, a następnie wybrany szablon jest używany do utworzenia zasad, które z kolei będą służyć do ochrony pliku.

**C++**:

    void PFileConverter::ConvertToPFileTemplates(const string           & userId,
                                             shared_ptr<istream>      inStream,
                                             const string           & fileExt,
                                             std::shared_ptr<iostream>outStream,
                                             IAuthenticationCallback& auth,
                                             IConsentCallback& /*consent*/,
                                             ITemplatesCallback     & templ)
    {
    auto templates = TemplateDescriptor::GetTemplateList(userId, auth);
    
    rmscore::modernapi::AppDataHashMap signedData;
    
    size_t pos = templ.SelectTemplate(templates);
    
    if (pos < templates.size()) {
    auto policy = UserPolicy::CreateFromTemplateDescriptor(
      templates[pos],
      userId,
      auth,
      USER_AllowAuditedExtraction,
      signedData);
   
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    }
    }

**Chroni plik na podstawie zasad**
**Źródło**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Opis**: tworzy strumień pliku chronionego, używając danych zasad, a następnie chroni plik.

**C++**:

    void PFileConverter::ConvertToPFileUsingPolicy(shared_ptr<UserPolicy>   policy,
                                               shared_ptr<istream>      inStream,
                                               const string           & fileExt,
                                               std::shared_ptr<iostream>outStream)
    {
    if (policy.get() != nullptr) {
    auto outIStream = rmscrypto::api::CreateStreamFromStdStream(outStream);
    auto pStream    = ProtectedFileStream::Create(policy, outIStream, fileExt);
    
    // preparing
    readPosition  = 0;
    writePosition = pStream->Size();
    
    inStream->seekg(0, ios::end);
    totalSize = inStream->tellg();
    
    // start threads
    for (size_t i = 0; i < THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(inStream),
                                  pStream,
                                  true));
    }
    
    for (thread& t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    
    pStream->Flush();
    }
    


## Scenariusz: zabezpieczenie pliku za pomocą ochrony niestandardowej

**Zabezpiecza plik za pomocą ochrony niestandardowej**
**Źródło**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Opis**: po otrzymaniu nazwy pliku od użytkownika, odczytaniu certyfikatów (zobacz *MainWindow::addCertificates*), zebraniu informacji o prawach od użytkownika i ustawieniu wywołania zwrotnego autoryzacji z identyfikatorem klienta i adresem URL przekierowania wybrany plik jest chroniony przez wywołanie *ConvertToPFilePredefinedRights* (zobacz poniższy przykład kodu).

**C++**:

    void MainWindow::ConvertToPFILEUsingRights(const string            & fileIn,
                                           const vector<UserRights>& userRights,
                                           const string            & clientId,
                                           const string            & redirectUrl,
                                           const string            & clientEmail)
    {
    // generate output filename
    string fileOut = fileIn + ".pfile";
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared<ifstream>(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared<fstream>(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileIn.c_str());
    return;
    }
    
    if (!outFile->is_open()) {
    AddLog("ERROR: Failed to open ", fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of('.');
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    // is anything to add
    if (userRights.size() == 0) {
    AddLog("ERROR: ", "Please fill email and check rights");
    return;
    }
    
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFilePredefinedRights(
      clientEmail,
      inFile,
      fileExt,
      outFile,
      auth,
      this->consent,
      userRights);
    
    AddLog("Successfully converted to ", fileOut.c_str());
    }
    catch (const rmsauth::Exception& e) {
    AddLog("ERROR: ", e.error().c_str());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    catch (const rmscore::exceptions::RMSException& e) {
    AddLog("ERROR: ", e.what());
    
    outFile->close();
    remove(fileOut.c_str());
    }
    inFile->close();
    outFile->close();
    }


**Tworzy zasady ochrony na podstawie wybranych praw użytkownika**
**Źródło**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Opis**: utwórz deskryptor zasad i uzupełnij go informacjami o prawach użytkownika, a następnie użyj deskryptora do utworzenia zasad dla użytkownika. Te zasady służą do ochrony wybranego pliku za pośrednictwem wywołania *ConvertToPFileUsingPolicy* (zobacz opis w poprzedniej sekcji niniejszego tematu).

**C++**:

    void PFileConverter::ConvertToPFilePredefinedRights(
    const string            & userId,
    shared_ptr<istream>       inStream,
    const string            & fileExt,
    shared_ptr<iostream>      outStream,
    IAuthenticationCallback & auth,
    IConsentCallback& /*consent*/,
    const vector<UserRights>& userRights)
    {
    auto endValidation = chrono::system_clock::now() + chrono::hours(48);
    
    
    PolicyDescriptor desc(userRights);
    
    desc.Referrer(make_shared<string>("https://client.test.app"));
    desc.ContentValidUntil(endValidation);
    desc.AllowOfflineAccess(false);
    desc.Name("Test Name");
    desc.Description("Test Description");
    
    auto policy = UserPolicy::Create(desc, userId, auth,
                                   USER_AllowAuditedExtraction);
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    

## WorkerThread — metoda wsparcia


Metoda *WorkerThread()* jest wywoływana przez dwa poprzednie przykładowe scenariusze; **Utwórz strumień pliku chronionego** i **Chroni plik na podstawie zasad** w następujący sposób:

**C++**:

    threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));


**Metoda wsparcia, WorkerThread()**

**C++**:

    static mutex   threadLocker;
    static int64_t totalSize     = 0;
    static int64_t readPosition  = 0;
    static int64_t writePosition = 0;
    static vector<thread> threadPool;
    
    static void WorkerThread(shared_ptr<iostream>           stdStream,
                         shared_ptr<ProtectedFileStream>pStream,
                         bool                           modeWrite) {
    vector<uint8_t> buffer(4096);
    int64_t bufferSize = static_cast<int64_t>(buffer.size());
    
    while (totalSize - readPosition > 0) {
    // lock
    threadLocker.lock();
    
    // check remain
    if (totalSize - readPosition <= 0) {
      threadLocker.unlock();
      return;
    }
    
    // get read/write offset
    int64_t offsetRead  = readPosition;
    int64_t offsetWrite = writePosition;
    int64_t toProcess   = min(bufferSize, totalSize - readPosition);
    readPosition  += toProcess;
    writePosition += toProcess;
    
    // no need to lock more
    threadLocker.unlock();
    
    if (modeWrite) {
      // stdStream is not thread safe!!!
      try {
        threadLocker.lock();
    
        stdStream->seekg(offsetRead);
        stdStream->read(reinterpret_cast<char *>(&buffer[0]), toProcess);
        threadLocker.unlock();
        auto written =
          pStream->WriteAsync(
            buffer.data(), toProcess, offsetWrite, std::launch::deferred).get();
    
        if (written != toProcess) {
          throw rmscore::exceptions::RMSStreamException("Error while writing data");
        }
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    } else {
      auto read =
        pStream->ReadAsync(&buffer[0],
                           toProcess,
                           offsetRead,
                           std::launch::deferred).get();
    
      if (read == 0) {
        break;
      }
    
      try {
        // stdStream is not thread safe!!!
        threadLocker.lock();
    
        // seek to write
        stdStream->seekp(offsetWrite);
        stdStream->write(reinterpret_cast<const char *>(buffer.data()), read);
        threadLocker.unlock();
      }
      catch (exception& e) {
        qDebug() << "Exception: " << e.what();
      }
    }
    }
    }


## Scenariusz: uwierzytelnianie za pomocą usługi RMS

W poniższych przykładach pokazano dwa różne podejścia do uwierzytelniania; uzyskiwanie tokenu uwierzytelniania Azure oAuth2 przy użyciu interfejsu użytkownika i bez niego.
**Uzyskiwanie tokenu uwierzytelniania oAuth2 przy użyciu interfejsu użytkownika**
**Źródło**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Krok 1**. Utwórz punkt udostępniany obiektu **rmsauth::FileCache**.
Opis: możesz ustawić ścieżkę pamięci podręcznej lub użyć domyślnej.

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**Krok 2**. Utwórz obiekt **rmsauth::AuthenticationContext**. Opis: określ *identyfikator URI uwierzytelniania* platformy Azure i obiekt *FileCache*.

**C++**:

    AuthenticationContext authContext(
                              std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                              AuthorityValidationType::False,
                              FileCachePtr);


**Krok 3**. Wywołaj metodę **aquireToken** obiektu **authContext** i określ następujące parametry: Opis:

-   *Żądany zasób* — chroniony zasób, do którego chcesz uzyskać dostęp
-   *Unikatowy identyfikator klienta* — zazwyczaj identyfikator GUID
-   *Identyfikator URI przekierowania* —identyfikator URI, który będzie przekierowany po pobraniu tokenu uwierzytelniania
-   *Zachowanie monitu uwierzytelniania* — jeśli ustawisz wartość **PromptBehavior::Auto**, biblioteka będzie próbować używać pamięci podręcznej i w razie potrzeby odświeżać token
-   *Identyfikator użytkownika* — nazwa użytkownika wyświetlana w oknie monitu

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                std::string(“https://client.test.app”),
                PromptBehavior::Auto,
                std::string(“john.smith@msopentechtest01.onmicrosoft.com”));


**Krok 4**. Uzyskaj token dostępu z wyników. Opis: wywołaj metodę **result-> accessToken()**

**Uwaga** Wszystkie metody biblioteki uwierzytelniania mogą zgłaszać wyjątek **rmsauth::Exception**.

 
**Uzyskiwanie tokenu uwierzytelniania oAuth2 bez interfejsu użytkownika**
**Źródło**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**Krok 1**. Utwórz punkt udostępniany obiektu **rmsauth::FileCache**. Opis: możesz ustawić ścieżkę pamięci podręcznej lub użyć domyślnej

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**Krok 2**. Utwórz obiekt **UserCredential**. Opis: określ *login użytkownika* i *hasło*

**C++**:

    auto userCred = std::make_shared<UserCredential>("john.smith@msopentechtest01.onmicrosoft.com",
                                                 "SomePass");


**Krok 3**. Utwórz obiekt **rmsauth::AuthenticationContext**. Opis: określ *identyfikator URI uwierzytelniania* platformy Azure i obiekt *FileCache*

**C++**:

    AuthenticationContext authContext(
                        std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                        AuthorityValidationType::False,
                        FileCachePtr);


**Krok 4**. Wywołaj metodę **aquireToken** obiektu **authContext** i określ parametry:
-   *Żądany zasób* — chroniony zasób, do którego chcesz uzyskać dostęp
-   *Unikatowy identyfikator klienta* — zazwyczaj identyfikator GUID
-   *Poświadczenia użytkownika* — przekaż utworzony obiekt

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                userCred);


**Krok 5**. Uzyskaj token dostępu z wyników. Opis: wywołaj metodę **result-> accessToken()**

**Uwaga** Wszystkie metody biblioteki uwierzytelniania mogą zgłaszać wyjątek **rmsauth::Exception**.




<!--HONumber=Aug16_HO1-->


