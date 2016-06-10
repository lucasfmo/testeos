---
# required metadata

title: Útmutató&#58; Hitelesítés hozzáadása az alkalmazásához | Azure RMS
description: Ismerteti az RMS-kompatibilis alkalmazások felhasználóhitelesítésének alapjait.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Útmutató: Hitelesítés hozzáadása az alkalmazásához

Ez a témakör ismerteti az RMS-kompatibilis alkalmazások felhasználóhitelesítésének alapjait.

## A felhasználóhitelesítés ismertetése
A felhasználóhitelesítés egy lényeges lépés az eszközalkalmazás és az RMS-infrastruktúra közötti kommunikáció létesítéséhez. Ez a hitelesítési folyamat a szabványos OAuth 2.0 protokollt használja, amelyhez az alábbi adatokra van szükség az aktuális felhasználóról és a hitelesítési kérelméről: **hitelesítésszolgáltató**, **erőforrás** és **felhasználói azonosító**.

**Megjegyzés**  A hatókör jelenleg nincs használatban, de később még lehet, és ezért a rendszer fenntartja a jövőbeli használatra.

 

**Felhasználóhitelesítés visszahívása** – A Microsoft Rights Management SDK 4.2 a hitelesítés-visszahívást megvalósítását fogja használni, amikor nem ad meg hozzáférési tokent, ha a hozzáférési token frissítésre szorul, vagy ha a hozzáférési token lejárt.

A platform összes RMS API-ja tartalmaz egy visszahívást, amelyet meg kell valósítani a felhasználóhitelesítés engedélyezéséhez.

-   Az Android API az [**AuthenticationRequestCallback**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_authenticationrequestcallback_interface_java) és az [**AuthenticationCompletionCallback**](/rights-management/sdk/4.2/api/android/authenticationcompletioncallback#msipcthin2_authenticationcompletioncallback_interface_java) interfészt használja.
-   Az iOS/OS X API az [**MSAuthenticationCallback**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msauthenticationcallback_protocol_objc) protokollt használja.
-   A WinPhone API az [**IAuthenticationCallback**](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_iauthenticationcallback) interfészt használja.
-   A Linux API az [IAuthenticationCallback](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html) interfészt használja.

## A hitelesítéshez használt könyvtár

A hitelesítés-visszahívás megvalósításához le kell tölteni egy megfelelő könyvtárat, majd konfigurálnia kell a fejlesztői környezetet annak használatára. Ezekhez a platformokhoz a GitHubon találhatja meg az ADAL könyvtárakat. Az alábbi források mindegyike tartalmaz útmutatást a környezet beállításához és a könyvtár használatához.

-   [Microsoft Azure Active Directory Authentication Library (ADAL) iOS rendszerhez](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Microsoft Azure Active Directory Authentication Library (ADAL) Mac géphez](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Microsoft Azure Active Directory Authentication Library (ADAL) Androidhoz](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)
-   [Microsoft Azure Active Directory Authentication Library (ADAL) dotnethez](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)
-   Linux SDK esetében az ADAL könyvtár az SDK-forrással együtt van csomagolva, és elérhető a [GitHubon](https://github.com/AzureAD/rms-sdk-for-cpp).

**Megjegyzés**  Javasoljuk valamelyik fenti Active Directory Authentication Library (ADAL) használatát, de használhat más hitelesítési könyvtárat is.

## Adatbevitel az Azure Active Directory Authentication Library (ADAL) segítségével történő hitelesítés esetén

Az ADAL több paraméter megadását igényli a felhasználó sikeres hitelesítéséhez az Azure RMS-en (vagy AD RMS-en). Ezek azok a szabványos OAuth 2.0-paraméterek, amelyekre általában szükség van minden Azure AD-alkalmazáshoz, többek között az RMS-kompatibilis alkalmazásokhoz. Az ADAL használatának aktuális irányelveit megtalálja a korábban felsorolt megfelelő Github-adattárak README fájljaiban.

Az RMS-munkafolyamatokhoz a következő paraméterekre és irányelvekre van szükség:

-   **Hitelesítésszolgáltató** – a hitelesítési végpont, általában az AAD vagy az ADFS URL-címe. Ezt a paramétert az RMS SDK hitelesítés-visszahívás biztosítja az alkalmazás számára.
-   **Erőforrás** – Az elérni kívánt szolgáltatásalkalmazás, általában az Azure RMS vagy az AD RMS URL-címe/URI azonosítója. Ezt a paramétert az RMS SDK hitelesítés-visszahívás biztosítja az alkalmazás számára.
-   **Felhasználói azonosító** – az alkalmazáshoz hozzáférni kívánó felhasználó egyszerű felhasználóneve, általában az e-mail-címe. Ez a paraméter lehet üres, ha a felhasználó még nem ismert, és ez használatos a felhasználói token gyorsítótárazására vagy egy token a gyorsítótárból való lekérésére is. Általában ez használatos általános tippként is a felhasználói adatkérésekhez.
-   **Ügyfél-azonosító** – az ügyfélalkalmazás azonosítója. Ennek egy érvényes Azure AD-alkalmazásazonosítónak kell lennie. További információk: How to: Get an Azure Application ID (Útmutató: Azure-alkalmazásazonosító beszerzése).
-   **Átirányítási URI** – megadja a hitelesítési könyvtárat egy URI-céllal a hitelesítési kódhoz. Vegye figyelembe, hogy az iOS és Android rendszerhez megadott formátumok szükségesek, amelyek leírása az ADAL megfelelő GitHub-adattáraiban lévő README fájlokban található.

    Android:: `msauth://packagename/Base64UrlencodedSignature`

    iOS: `<app-scheme>://<bundle-id>`

**Megjegyzés**  Ha az alkalmazása nem követi ezeket az irányelveket, az Azure RMS- és az Azure AD-munkafolyamatok valószínűleg nem fognak működni, és a Microsoft.com nem támogatja azokat. Emellett a Rights Management Licencszerződés (RMLA) megsértése következhet be, ha érvénytelen ügyfélazonosítót használ egy éles alkalmazásban.

## A hitelesítés-visszahívás megvalósításának bemutatása

**Hitelesítésikód-példák** – Ez az SDK példakóddal mutatja be a hitelesítés-visszahívások használatát. Az Ön kényelme érdekében ezek a példakódok itt is és az alább hivatkozott témakörökben is szerepelnek.

**Android-felhasználóhitelesítés** – további információk: [Android code examples](android-code.md) (Android-kódpéldák), az első, „Consuming an RMS protected file” (RMS-védelemmel ellátott fájlok használata) című forgatókönyv **2. lépése**.


    class MsipcAuthenticationCallback implements AuthenticationRequestCallback
    {
    ...

    @Override
    public void getToken(Map<String, String> authenticationParametersMap,
                         final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
    {
        String authority = authenticationParametersMap.get("oauth2.authority");
        String resource = authenticationParametersMap.get("oauth2.resource");
        String userId = authenticationParametersMap.get("userId");
        mClientId = “12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”; // get your registered Azure AD application ID here
        mRedirectUri = “urn:ietf:wg:oauth:2.0:oob”;
        final String userHint = (userId == null)? "" : userId;
        AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
        if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
        {
            try
            {
                authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                App.getInstance().setAuthenticationContext(authenticationContext);
            }
            catch (NoSuchAlgorithmException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
            catch (NoSuchPaddingException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
       }
        App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                       "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                        {
                            @Override
                            public void onError(Exception exc)
                            {
                                …
                                if (exc instanceof AuthenticationCancelError)
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onCancel();
                                }
                                else
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onFailure();
                                }
                            }

                            @Override
                            public void onSuccess(AuthenticationResult result)
                            {
                                …
                                if (result == null || result.getAccessToken() == null
                                        || result.getAccessToken().isEmpty())
                                {
                                     …
                                }
                                else
                                {
                                    // request is successful
                                    …
                                    authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                }
                            }
                        });
                         }


**iOS-/OS X-felhasználóhitelesítés** – további információk: [iOS/OS X code examples](ios-os-x-code-examples.md) (iOS-/OS X-kódpéldák).

Az első, „Consuming an RMS protected file” (RMS-védelemmel ellátott fájlok használata) című forgatókönyv **2. lépése**.


    // AuthenticationCallback holds the necessary information to retrieve an access token.
    @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

    @end

    @implementation MsipcAuthenticationCallback

    - (void)accessTokenWithAuthenticationParameters:
         (MSAuthenticationParameters *)authenticationParameters
                                completionBlock:
         (void(^)(NSString *accessToken, NSError *error))completionBlock
    {
    ADAuthenticationError *error;
    ADAuthenticationContext* context = [ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority error:&error];

    NSString *appClientId = @”12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”;

    // get your registered Azure AD application ID here

    NSURL *redirectURI = [NSURL URLWithString:@”ms-sample://com.microsoft.sampleapp”];

    // get your <app-scheme>://<bundle-id> here
    // Retrieve token using ADAL
    [context acquireTokenWithResource:authenticationParameters.resource
                             clientId:appClientId
                          redirectUri:redirectURI
                               userId:authenticationParameters.userId
                      completionBlock:^(ADAuthenticationResult *result)
                      {
                          if (result.status != AD_SUCCEEDED)
                          {
                              NSLog(@"Auth Failed");
                              completionBlock(nil, result.error);
                          }
                          else
                          {
                              completionBlock(result.accessToken, result.error);
                          }
                      }

        ];
    }



**Linux- / C++-felhasználóhitelesítés** – további információk: [Linux code examples](linux-c-code-examples.md) (Linux kódpéldák).



    // Class Header
    class AuthCallback : public IAuthenticationCallback {
    private:

      std::shared_ptr<rmsauth::FileCache> FileCachePtr;
      std::string clientId_;
      std::string redirectUrl_;

      public:

      AuthCallback(const std::string& clientId,
               const std::string& redirectUrl);
      virtual std::string GetToken(shared_ptr<AuthenticationParameters>& ap) override;
    };

    class ConsentCallback : public IConsentCallback {
      public:

      virtual ConsentList Consents(ConsentList& consents) override;
    };

    // Class Implementation
    AuthCallback::AuthCallback(const string& clientId, const string& redirectUrl)
    : clientId_(clientId), redirectUrl_(redirectUrl) {
      FileCachePtr = std::make_shared<FileCache>();
    }

    string AuthCallback::GetToken(shared_ptr<AuthenticationParameters>& ap)
    {
      string redirect =
      ap->Scope().empty() ? redirectUrl_ : ap->Scope();

      try
      {
        if (redirect.empty()) {
        throw rmscore::exceptions::RMSInvalidArgumentException(
              "redirect Url is empty");
      }

      if (clientId_.empty()) {
      throw rmscore::exceptions::RMSInvalidArgumentException("client Id is empty");
      }

      AuthenticationContext authContext(
        ap->Authority(), AuthorityValidationType::False, FileCachePtr);

      auto result = authContext.acquireToken(ap->Resource(),
                                           clientId_, redirect,
                                           PromptBehavior::Auto,
                                           ap->UserId());
      return result->accessToken();
      }

      catch (const rmsauth::Exception& ex)
      {
        // out logs
        throw;
      }
    }



 

 


<!--HONumber=Apr16_HO4-->


