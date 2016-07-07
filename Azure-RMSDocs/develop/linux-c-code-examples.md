---
title: "Linux-kódpéldák | Azure RMS"
description: "Ez a témakör az RMS SDK Linux-verziójának fontos forgatókönyveit és kódelemeit mutatja be."
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
ms.sourcegitcommit: 79e58b8092ea7cb057229d4c464d79f3694296e6
ms.openlocfilehash: ace7103cfb44d84a7dd6bf64f57c2a47530117e0


---

# Linux code examples (Linux-kódpéldák)

Ez a témakör az RMS SDK Linux-verziójának fontos forgatókönyveit és kódelemeit mutatja be.

Az alábbi kódrészletek az *rms\_sample* és az *rmsauth\_sample* mintaalkalmazásból származnak. További információkért lásd a GitHub-tárházban szereplő [mintákat](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples).

## Forgatókönyv: Egy védett fájl védelmi házirendjére vonatkozó információk elérése

**Megnyit és elolvas egy RMS-védelemmel ellátott fájlt**
**Forrás**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: A felhasználó által megadott fájlnév lekérése, a tanúsítványok olvasása (lásd: *MainWindow::addCertificates*), az ügyfél-azonosító és az átirányítási URL-cím segítségével történő engedély-visszahívás beállítása után a *ConvertFromPFile* hívása (lásd az alábbi kódpéldát), majd a védelmi házirend nevének, leírásának és tartalom-érvényességi dátumának olvasása.

**C++**:

    void MainWindow::ConvertFromPFILE(const string&amp; fileIn,
        const string&amp; clientId,
        const string&amp; redirectUrl,
        const string&amp; clientEmail) 
    {
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared&lt;ifstream&gt;(
    fileIn, ios_base::in | ios_base::binary);
    
    if (!inFile-&gt;is_open()) {
     AddLog(&quot;ERROR: Failed to open &quot;, fileIn.c_str());
    return;
    }
    
    string fileOut;
    
    // generate output filename
    auto pos = fileIn.find_last_of(&#39;.&#39;);
    
    if (pos != string::npos) {
     fileOut = fileIn.substr(0, pos);
    }
    
     // create streams
    auto outFile = make_shared&lt;fstream&gt;(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!outFile-&gt;is_open()) {
     AddLog(&quot;ERROR: Failed to open &quot;, fileOut.c_str());
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
      this-&gt;consent);
    
    AddLog(&quot;Successfully converted to &quot;, fileOut.c_str());
    }
    catch (const rmsauth::Exception&amp; e)
    {
    AddLog(&quot;ERROR: &quot;, e.error().c_str());
    }
    catch (const rmscore::exceptions::RMSException&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.what());
    }
    inFile-&gt;close();
    outFile-&gt;close();
    }

**Hozzon létre egy védett fájlfolyamot**
**Forrás**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: Ez a metódus a háttérben átadott folyamból védett fájlfolyamot hoz létre az SDK-metódussal (*ProtectedFileStream::Aquire*), amely ezután visszaérkezik a hívóhoz.

**C++**:

    shared_ptr&lt;GetProtectedFileStreamResult&gt;PFileConverter::ConvertFromPFile(
    const string           &amp; userId,
    shared_ptr&lt;istream&gt;      inStream,
    shared_ptr&lt;iostream&gt;     outStream,
    IAuthenticationCallback&amp; auth,
    IConsentCallback       &amp; consent)
    {
    auto inIStream = rmscrypto::api::CreateStreamFromStdStream(inStream);
    
    auto fsResult = ProtectedFileStream::Acquire(
    inIStream,
    userId,
    auth,
    consent,
    POL_None,
    static_cast&lt;ResponseCacheFlags&gt;(RESPONSE_CACHE_INMEMORY
                                    | RESPONSE_CACHE_ONDISK));
    
    if ((fsResult.get() != nullptr) &amp;&amp; (fsResult-&gt;m_status == Success) &amp;&amp;
      (fsResult-&gt;m_stream != nullptr)) {
    auto pfs = fsResult-&gt;m_stream;
    
    // preparing
    readPosition  = 0;
    writePosition = 0;
    totalSize     = pfs-&gt;Size();
    
    // start threads
    for (size_t i = 0; i &lt; THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast&lt;iostream&gt;(outStream), pfs,
                                  false));
    }
    
    for (thread&amp; t: threadPool) {
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

    void MainWindow::ConvertToPFILEUsingTemplates(const string&amp; fileIn,
                                              const string&amp; clientId,
                                              const string&amp; redirectUrl,
                                              const string&amp; clientEmail) 
    {
    // generate output filename
    string fileOut = fileIn + &quot;.pfile&quot;;
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared&lt;ifstream&gt;(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared&lt;fstream&gt;(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileIn.c_str());
    return;
    }
    
    if (!outFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of(&#39;.&#39;);
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    try {
    // create authentication callback
    AuthCallback auth(clientId, redirectUrl);
    
    // process convertion
    PFileConverter::ConvertToPFileTemplates(
      clientEmail, inFile, fileExt, outFile, auth,
      this-&gt;consent, this-&gt;templates);
    
    AddLog(&quot;Successfully converted to &quot;, fileOut.c_str());
    }
   catch (const rmsauth::Exception&amp; e) { AddLog(&quot;ERROR: &quot;, e.error().c_str()); outFile-&gt;close(); remove(fileOut.c_str()); } catch (const rmscore::exceptions::RMSException&amp; e) { AddLog(&quot;ERROR: &quot;, e.what());
    
    outFile-&gt;close();
    remove(fileOut.c_str());
    }
    inFile-&gt;close();
    outFile-&gt;close();
    }


**Sablonból létrehozott házirend segítségével véd egy fájlt**
**Forrás**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: Beolvassa a felhasználóhoz társított sablonok listáját, és a kiválasztott sablonból létrehoz egy házirendet, amely megvédi a fájlt.

**C++**:

    void PFileConverter::ConvertToPFileTemplates(const string           &amp; userId,
                                             shared_ptr&lt;istream&gt;      inStream,
                                             const string           &amp; fileExt,
                                             std::shared_ptr&lt;iostream&gt;outStream,
                                             IAuthenticationCallback&amp; auth,
                                             IConsentCallback&amp; /*consent*/,
                                             ITemplatesCallback     &amp; templ)
    {
    auto templates = TemplateDescriptor::GetTemplateList(userId, auth);
    
    rmscore::modernapi::AppDataHashMap signedData;
    
    size_t pos = templ.SelectTemplate(templates);
    
    if (pos &lt; templates.size()) {
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

    void PFileConverter::ConvertToPFileUsingPolicy(shared_ptr&lt;UserPolicy&gt;   policy,
                                               shared_ptr&lt;istream&gt;      inStream,
                                               const string           &amp; fileExt,
                                               std::shared_ptr&lt;iostream&gt;outStream)
    {
    if (policy.get() != nullptr) {
    auto outIStream = rmscrypto::api::CreateStreamFromStdStream(outStream);
    auto pStream    = ProtectedFileStream::Create(policy, outIStream, fileExt);
    
    // preparing
    readPosition  = 0;
    writePosition = pStream-&gt;Size();
    
    inStream-&gt;seekg(0, ios::end);
    totalSize = inStream-&gt;tellg();
    
    // start threads
    for (size_t i = 0; i &lt; THREADS_NUM; ++i) {
      threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast&lt;iostream&gt;(inStream),
                                  pStream,
                                  true));
    }
    
    for (thread&amp; t: threadPool) {
      if (t.joinable()) {
        t.join();
      }
    }
    
    pStream-&gt;Flush();
    }
    


## Forgatókönyv: Egy fájl védelme egyéni védelemmel

**Egyéni védelemmel véd egy fájlt**
**Forrás**: [rms\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: A felhasználótól által megadott fájlnév lekérése, a tanúsítványok olvasása (lásd: *MainWindow::addCertificates*), a felhasználótól származó jogosultsági információk begyűjtése, valamint az ügyfél-azonosító és az átirányítási URL-cím segítségével történő engedély-visszahívás beállítása után a kiválasztott fájl védelme a *ConvertToPFilePredefinedRights* hívásával (lásd az alábbi kódpéldát).

**C++**:

    void MainWindow::ConvertToPFILEUsingRights(const string            &amp; fileIn,
                                           const vector&lt;UserRights&gt;&amp; userRights,
                                           const string            &amp; clientId,
                                           const string            &amp; redirectUrl,
                                           const string            &amp; clientEmail)
    {
    // generate output filename
    string fileOut = fileIn + &quot;.pfile&quot;;
    
    // add trusted certificates using HttpHelpers of RMS and Auth SDKs
    addCertificates();
    
    // create shared in/out streams
    auto inFile = make_shared&lt;ifstream&gt;(
    fileIn, ios_base::in | ios_base::binary);
    auto outFile = make_shared&lt;fstream&gt;(
    fileOut, ios_base::in | ios_base::out | ios_base::trunc | ios_base::binary);
    
    if (!inFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileIn.c_str());
    return;
    }
    
    if (!outFile-&gt;is_open()) {
    AddLog(&quot;ERROR: Failed to open &quot;, fileOut.c_str());
    return;
    }
    
    // find file extension
    string fileExt;
    auto   pos = fileIn.find_last_of(&#39;.&#39;);
    
    if (pos != string::npos) {
    fileExt = fileIn.substr(pos);
    }
    
    // is anything to add
    if (userRights.size() == 0) {
    AddLog(&quot;ERROR: &quot;, &quot;Please fill email and check rights&quot;);
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
      this-&gt;consent,
      userRights);
    
    AddLog(&quot;Successfully converted to &quot;, fileOut.c_str());
    }
    catch (const rmsauth::Exception&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.error().c_str());
    
    outFile-&gt;close();
    remove(fileOut.c_str());
    }
    catch (const rmscore::exceptions::RMSException&amp; e) {
    AddLog(&quot;ERROR: &quot;, e.what());
    
    outFile-&gt;close();
    remove(fileOut.c_str());
    }
    inFile-&gt;close();
    outFile-&gt;close();
    }


**Védelmi házirendet hoz létre, amely adott jogokat biztosít a felhasználó számára**
**Forrás**: [rms\_sample/pfileconverter.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rms_sample)

**Leírás**: Házirendleíró létrehozása és kitöltése a felhasználó jogosultsági adataival, majd egy felhasználói házirend létrehozása a házirendleíró segítségével. Ezzel a házirenddel a *ConvertToPFileUsingPolicy* hívásával védhető meg a kiválasztott fájl (ennek leírását a jelen témakör egy korábbi szakaszában találja).

**C++**:

    void PFileConverter::ConvertToPFilePredefinedRights(
    const string            &amp; userId,
    shared_ptr&lt;istream&gt;       inStream,
    const string            &amp; fileExt,
    shared_ptr&lt;iostream&gt;      outStream,
    IAuthenticationCallback &amp; auth,
    IConsentCallback&amp; /*consent*/,
    const vector&lt;UserRights&gt;&amp; userRights)
    {
    auto endValidation = chrono::system_clock::now() + chrono::hours(48);
    
    
    PolicyDescriptor desc(userRights);
    
    desc.Referrer(make_shared&lt;string&gt;(&quot;https://client.test.app&quot;));
    desc.ContentValidUntil(endValidation);
    desc.AllowOfflineAccess(false);
    desc.Name(&quot;Test Name&quot;);
    desc.Description(&quot;Test Description&quot;);
    
    auto policy = UserPolicy::Create(desc, userId, auth,
                                   USER_AllowAuditedExtraction);
    ConvertToPFileUsingPolicy(policy, inStream, fileExt, outStream);
    

## WorkerThread – támogatási metódus


A *WorkerThread()* metódust az előbbi példák közül két forgatókönyv hívhatja: a **Védett fájlfolyam létrehozása**, valamint a **Fájl védelme házirenddel**, az alábbi módon:

**C++**:

    threadPool.push_back(thread(WorkerThread,
                                  static_pointer_cast&lt;iostream&gt;(outStream), pfs,
                                  false));


**Támogatási módszer, WorkerThread()**

**C++**:

    static mutex   threadLocker;
    static int64_t totalSize     = 0;
    static int64_t readPosition  = 0;
    static int64_t writePosition = 0;
    static vector&lt;thread&gt; threadPool;
    
    static void WorkerThread(shared_ptr&lt;iostream&gt;           stdStream,
                         shared_ptr&lt;ProtectedFileStream&gt;pStream,
                         bool                           modeWrite) {
    vector&lt;uint8_t&gt; buffer(4096);
    int64_t bufferSize = static_cast&lt;int64_t&gt;(buffer.size());
    
    while (totalSize - readPosition &gt; 0) {
    // lock
    threadLocker.lock();
    
    // check remain
    if (totalSize - readPosition &lt;= 0) {
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
    
        stdStream-&gt;seekg(offsetRead);
        stdStream-&gt;read(reinterpret_cast&lt;char *&gt;(&amp;buffer[0]), toProcess);
        threadLocker.unlock();
        auto written =
          pStream-&gt;WriteAsync(
            buffer.data(), toProcess, offsetWrite, std::launch::deferred).get();
    
        if (written != toProcess) {
          throw rmscore::exceptions::RMSStreamException(&quot;Error while writing data&quot;);
        }
      }
      catch (exception&amp; e) {
        qDebug() &lt;&lt; &quot;Exception: &quot; &lt;&lt; e.what();
      }
    } else {
      auto read =
        pStream-&gt;ReadAsync(&amp;buffer[0],
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
        stdStream-&gt;seekp(offsetWrite);
        stdStream-&gt;write(reinterpret_cast&lt;const char *&gt;(buffer.data()), read);
        threadLocker.unlock();
      }
      catch (exception&amp; e) {
        qDebug() &lt;&lt; &quot;Exception: &quot; &lt;&lt; e.what();
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

    auto FileCachePtr = std::make_shared&lt; rmsauth::FileCache&gt;();


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


**4. lépés**: Szerezze be a hozzáférési tokent az eredményből. Leírás: Hívja meg a **result-&gt; accessToken()** metódust.

**Megjegyzés**: A hitelesítésikönyvtár-metódusok bármelyike kiválthatja a következőt: **rmsauth::Exception**

 
**Az oAuth2 hitelesítési token beszerzése a felhasználói felület nélkül**
**Forrás**: [rmsauth\_sample/mainwindow.cpp](https://github.com/AzureAD/rms-sdk-for-cpp/tree/master/samples/rmsauth_sample)

**1. lépés**: Hozza létre az **rmsauth::FileCache** objektum megosztási pontját. Leírás: Megadhatja a gyorsítótár elérési útját, vagy használhatja az alapértelmezettet.

**C++**:

    auto FileCachePtr = std::make_shared&lt; rmsauth::FileCache&gt;();


**2. lépés**: Hozza létre a **UserCredential** objektumot. Leírás: Adja meg a *felhasználónevet* és a *jelszót*.

**C++**:

    auto userCred = std::make_shared&lt;UserCredential&gt;(&quot;john.smith@msopentechtest01.onmicrosoft.com&quot;,
                                                 &quot;SomePass&quot;);


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


**5. lépés**: Szerezze be a hozzáférési tokent az eredményből. Leírás: Hívja meg a **result-&gt; accessToken()** metódust.

**Megjegyzés**: A hitelesítésikönyvtár-metódusok bármelyike kiválthatja a következőt: **rmsauth::Exception**




<!--HONumber=Jun16_HO4-->


