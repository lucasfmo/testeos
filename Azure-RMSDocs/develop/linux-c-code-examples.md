---
title: "Linux-kódpéldák | Azure RMS"
description: "Ez a témakör az RMS SDK Linux-verziójának fontos forgatókönyveit és kódelemeit mutatja be."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0F7714CA-1D3E-4846-B187-739825B7DE26
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 0d63a47f15d4ef08d9e17a0416f9d6f06536b6aa


---

# Linux code examples (Linux-kódpéldák)

Ez a témakör az RMS SDK Linux-verziójának fontos forgatókönyveit és kódelemeit mutatja be.

Az alábbi kódrészletek az *rms\_sample* és az *rmsauth\_sample* mintaalkalmazásból származnak. További információkért lásd a GitHub-tárházban szereplő [mintákat](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples).

## Forgatókönyv: Egy védett fájl védelmi házirendjére vonatkozó információk elérése

**Megnyit és elolvas egy RMS-védelemmel ellátott fájlt**
**Forrás**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: A felhasználó által megadott fájlnév lekérése, a tanúsítványok olvasása (lásd: *MainWindow::addCertificates*), az ügyfél-azonosító és az átirányítási URL-cím segítségével történő engedély-visszahívás beállítása után a *ConvertFromPFile* hívása (lásd az alábbi kódpéldát), majd a védelmi házirend nevének, leírásának és tartalom-érvényességi dátumának olvasása.

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

**Hozzon létre egy védett fájlfolyamot**
**Forrás**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: Ez a metódus a háttérben átadott folyamból védett fájlfolyamot hoz létre az SDK-metódussal (*ProtectedFileStream::Aquire*), amely ezután visszaérkezik a hívóhoz.

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

## Forgatókönyv: Új védett fájl létrehozása sablon használatával

**Felhasználó által kijelölt sablonnal véd egy fájlt**
**Forrás**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: A felhasználó által megadott fájlnév lekérése, a tanúsítványok olvasása (lásd: *MainWindow::addCertificates*), valamint az ügyfél-azonosító és az átirányítási URL-cím segítségével történő engedély-visszahívás beállítása után a kiválasztott fájl védelme a *ConvertToPFileTemplates* hívásával (lásd az alábbi kódpéldát).

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


**Sablonból létrehozott házirend segítségével véd egy fájlt**
**Forrás**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: Beolvassa a felhasználóhoz társított sablonok listáját, és a kiválasztott sablonból létrehoz egy házirendet, amely megvédi a fájlt.

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

**Egy adott házirend segítségével véd egy fájlt**
**Forrás**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: Védett fájlfolyam létrehozása az adott házirenddel, majd a fájl védelme.

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
    


## Forgatókönyv: Egy fájl védelme egyéni védelemmel

**Egyéni védelemmel véd egy fájlt**
**Forrás**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: A felhasználótól által megadott fájlnév lekérése, a tanúsítványok olvasása (lásd: *MainWindow::addCertificates*), a felhasználótól származó jogosultsági információk begyűjtése, valamint az ügyfél-azonosító és az átirányítási URL-cím segítségével történő engedély-visszahívás beállítása után a kiválasztott fájl védelme a *ConvertToPFilePredefinedRights* hívásával (lásd az alábbi kódpéldát).

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


**Védelmi házirendet hoz létre, amely adott jogokat biztosít a felhasználó számára**
**Forrás**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: Házirendleíró létrehozása és kitöltése a felhasználó jogosultsági adataival, majd egy felhasználói házirend létrehozása a házirendleíró segítségével. Ezzel a házirenddel a *ConvertToPFileUsingPolicy* hívásával védhető meg a kiválasztott fájl (ennek leírását a jelen témakör egy korábbi szakaszában találja).

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
    

## WorkerThread – támogatási metódus


A *WorkerThread()* metódust az előbbi példák közül két forgatókönyv hívhatja: a **Védett fájlfolyam létrehozása**, valamint a **Fájl védelme házirenddel**, az alábbi módon:

**C++**:

    threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast<iostream>(outStream), pfs,
                                  false));


**Támogatási módszer, WorkerThread()**

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


## Forgatókönyv: RMS-hitelesítés

Az alábbi példák két különböző hitelesítési módot mutatnak be: az Azure hitelesítési oAuth2 token beszerzését a felhasználói felületen keresztül, valamint anélkül.
**Az oAuth2 hitelesítési token beszerzése a felhasználói felületen keresztül**
**Forrás**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**1. lépés**: Hozzon létre egy megosztott pontot az **rmsauth::FileCache** objektumhoz.
Leírás: Beállíthatja a gyorsítótár elérési útját vagy használhatja az alapértelmezettet.

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**2. lépés**: hozzon létre **rmsauth::AuthenticationContext** objektumot. Leírás: Adja meg Azure *hitelesítésszolgáltatói URI-jét* és *FileCache* objektumát.

**C++**:

    AuthenticationContext authContext(
                              std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                              AuthorityValidationType::False,
                              FileCachePtr);


**3. lépés**: Hívja meg az **authContext** objektum **aquireToken** metódusát, és adja meg a következő paramétereket: Leírás:

-   *Kért erőforrás* – az elérni kívánt védett erőforrás
-   *Ügyfél egyedi azonosítója* – általában egy GUID azonosító
-   *Átirányítási URI* – az az URI, amely a hitelesítési token beszerzése után módosítva lesz
-   *Hitelesítési parancssor viselkedése* – a **PromptBehavior::Auto** érték megadása esetén a könyvtár szükség esetén megkísérli a gyorsítótárazási és a frissítési token használatát
-   *Felhasználói azonosító* – A parancsablakban megjelenő felhasználónév

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                std::string(“https://client.test.app”),
                PromptBehavior::Auto,
                std::string(“john.smith@msopentechtest01.onmicrosoft.com”));


**4. lépés**: Szerezze be a hozzáférési tokent az eredményből. Leírás: Hívja meg a **result-> accessToken()** metódust

**Megjegyzés**: A hitelesítésikönyvtár-metódusok bármelyike kiválthatja a következőt: **rmsauth::Exception**

 
**Az oAuth2 hitelesítési token beszerzése a felhasználói felület nélkül**
**Forrás**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**1. lépés**: Hozza létre az **rmsauth::FileCache** objektum megosztási pontját. Leírás: Megadhatja a gyorsítótár elérési útját, vagy használhatja az alapértelmezettet.

**C++**:

    auto FileCachePtr = std::make_shared< rmsauth::FileCache>();


**2. lépés**: Hozza létre a **UserCredential** objektumot. Leírás: Adja meg a *felhasználónevet* és a *jelszót*.

**C++**:

    auto userCred = std::make_shared<UserCredential>("john.smith@msopentechtest01.onmicrosoft.com",
                                                 "SomePass");


**3. lépés**: Hozza létre az **rmsauth::AuthenticationContext** objektumot. Leírás: Adja meg az Azure hitelesítésszolgáltatói *URI* és *FileCache* objektumot.

**C++**:

    AuthenticationContext authContext(
                        std::string(“https://sts.aadrm.com/_sts/oauth/authorize”),
                        AuthorityValidationType::False,
                        FileCachePtr);


**4. lépés**: Hívja az **authContext** objektum **aquireToken** metódusát, és adja meg a paramétereket:
-   *Kért erőforrás* – az elérni kívánt védett erőforrás
-   *Ügyfél egyedi azonosítója* – általában egy GUID azonosító
-   *Felhasználói hitelesítő adatok* – a létrehozott objektum átadása

**C++**:

    auto result = authContext.acquireToken(
                std::string(“api.aadrm.com”),
                std::string(“4a63455a-cfa1-4ac6-bd2e-0d046cf1c3f7”),
                userCred);


**5. lépés**: Szerezze be a hozzáférési tokent az eredményből. Leírás: Hívja meg a **result-> accessToken()** metódust

**Megjegyzés**: A hitelesítésikönyvtár-metódusok bármelyike kiválthatja a következőt: **rmsauth::Exception**




<!--HONumber=Aug16_HO4-->


