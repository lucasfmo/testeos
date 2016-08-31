---
title: "Az alkalmazás regisztrálása és RMS-kompatibilissé tétele az Azure AD-vel | Azure RMS"
description: "Ismerteti az RMS-kompatibilis alkalmazások felhasználóhitelesítésének alapjait."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 07/07/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5d2339ece646fc51410186d43facdea28ac8fdfe
ms.openlocfilehash: 87ffcdaeaae80efa23c0ed7e7ce95ac7f63c62e0


---

# Az alkalmazás regisztrálása és RMS-kompatibilissé tétele az Azure AD-vel

Ez a témakör végigvezeti Önt az Azure-portálos alkalmazásregisztráció és RMS-kompatibilitás alapjain, majd az Azure Active Directory Authentication Library-vel (ADAL) való felhasználói hitelesítés folyamatán.

## A felhasználóhitelesítés ismertetése
A felhasználóhitelesítés egy lényeges lépés az eszközalkalmazás és az RMS-infrastruktúra közötti kommunikáció létesítéséhez. Ez a hitelesítési folyamat a szabványos OAuth 2.0 protokollt használja, amelyhez kulcsfontosságú adatokra van szükség az aktuális felhasználóról és a hitelesítési kérelemről.

## Regisztráció az Azure-portálon
Elsőként tekintse meg ezt az útmutatót az alkalmazás regisztrálásának az Azure-portálon való konfigurálásról: [Az Azure RMS konfigurálása ADAL-hitelesítéshez](adal-auth.md). A folyamat során másolja ki és mentse el az **ügyfél-azonosítót** és **átirányítási URI-t** későbbi használatra.

## Rights Management-licencszerződés (RMLA) beszerzése
Az alkalmazás telepítése előtt RMLA-licencszerződést kell kötnie a Microsoft Rights Management-csapatával. A szerződésre vonatkozó további információkat jelen témakör [Éles üzembe helyezés – Üzemi használatra szóló licencszerződés kérése](deploying-your-application.md) című szakaszában talál.

## A felhasználói hitelesítés implementálása az alkalmazásban
Az összes RMS API tartalmaz egy visszahívást, amelyet meg kell valósítani a felhasználóhitelesítés engedélyezéséhez. Az RMS SDK 4.2 a visszahívás megvalósítását fogja használni akkor, ha nem ad meg hozzáférési tokent, ha a hozzáférési token frissítésre szorul, vagy ha a hozzáférési token lejárt.

- Android – [AuthenticationRequestCallback](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_authenticationrequestcallback_interface_java) és az [AuthenticationCompletionCallback](/rights-management/sdk/4.2/api/android/authenticationcompletioncallback#msipcthin2_authenticationcompletioncallback_interface_java) felületek.
- iOS / OS X – [MSAuthenticationCallback](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msauthenticationcallback_protocol_objc) protokoll.
-  Windows Phone / Windows RT –  [IAuthenticationCallback](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_iauthenticationcallback) felület.
- Linux – [IAuthenticationCallback](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html) felület.

### A hitelesítéshez használt könyvtár
A hitelesítés-visszahívás megvalósításához le kell tölteni egy megfelelő könyvtárat, majd konfigurálnia kell a fejlesztői környezetet annak használatára. Ezekhez a platformokhoz a GitHubon találhatja meg az ADAL könyvtárakat.

Az alábbi források mindegyike tartalmaz útmutatást a környezet beállításához és a könyvtár használatához.

-   [Microsoft Azure Active Directory Authentication Library (ADAL) iOS rendszerhez](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Microsoft Azure Active Directory Authentication Library (ADAL) Mac géphez](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Microsoft Azure Active Directory Authentication Library (ADAL) Androidhoz](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)
-   [Microsoft Azure Active Directory Authentication Library (ADAL) dotnethez](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)
-   Linux SDK esetében az ADAL könyvtár az SDK-forrással együtt van csomagolva, és elérhető a [GitHubon](https://github.com/AzureAD/rms-sdk-for-cpp).

>[!NOTE]  
> Javasoljuk valamelyik ADAL használatát, de használhat más hitelesítési könyvtárat is.

### Hitelesítési paraméterek

Az ADAL-nak több adatra is szüksége van a felhasználó sikeres hitelesítéséhez az Azure RMS-en (vagy AD RMS-en). Ezek szabványos OAuth 2.0-paraméterek, és általában szükség van rájuk minden Azure AD-alkalmazáshoz. Az ADAL használatának aktuális irányelveit megtalálja a korábban felsorolt megfelelő Github-adattárak README fájljaiban.

- **Hitelesítésszolgáltató** – a hitelesítési végpont, általában az AAD vagy az ADFS URL-címe.
- **Erőforrás** – Az elérni kívánt szolgáltatásalkalmazás, általában az Azure RMS vagy az AD RMS URL-címe/URI azonosítója.
- **Felhasználói azonosító** – az alkalmazáshoz hozzáférni kívánó felhasználó egyszerű felhasználóneve, általában az e-mail-címe. Ez a paraméter lehet üres, ha a felhasználó még nem ismert, és ez használatos a felhasználói token gyorsítótárazására vagy egy token a gyorsítótárból való lekérésére is. Ez sokszor használatos általános *tippként* is a felhasználói adatkérésekhez.
- **Ügyfél-azonosító** – az ügyfélalkalmazás azonosítója. Ennek egy érvényes Azure AD-alkalmazásazonosítónak kell lennie.
És az Azure-portál előző regisztrációs lépésében található.
- **Átirányítási URI** – megadja a hitelesítési könyvtárat egy URI-céllal a hitelesítési kódhoz. Az iOS és az Android rendszerekhez különleges formátumok szükségesek. Ezekről további információt az ADAL megfelelő Github-adattárainak README fájljaiban találhat. Ez az érték az Azure-portál előző regisztrációs lépésében található.

>[!NOTE] 
> A **hatókör** jelenleg nincs használatban, de később még lehet, és ezért a rendszer fenntartja a jövőbeli használatra.

    Android: `msauth://packagename/Base64UrlencodedSignature`

    iOS: `<app-scheme>://<bundle-id>`

>[!NOTE] 
> Ha az alkalmazása nem követi ezeket az irányelveket, az Azure RMS- és az Azure AD-munkafolyamatok valószínűleg nem fognak működni, és a Microsoft.com nem támogatja azokat. Emellett a Rights Management Licencszerződés (RMLA) megsértése következhet be, ha érvénytelen ügyfélazonosítót használ egy éles alkalmazásban.

### A hitelesítés-visszahívás megvalósításának bemutatása
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


**iOS/OS X-felhasználóhitelesítés** – további információ: [iOS/OS X code examples](ios-os-x-code-examples.md) (iOS/OS X-kódpéldák), *az első forgatókönyv, a Consuming an RMS protected file (RMS-védelemmel ellátott fájlok használata) 2. lépése.*


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



**Linux-felhasználóhitelesítés** – további információ: [Linux code examples](linux-c-code-examples.md) (Linux kódpéldák).



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



 

 



<!--HONumber=Aug16_HO4-->


