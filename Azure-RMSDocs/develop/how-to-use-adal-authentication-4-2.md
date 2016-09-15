---
title: "Konfigurowanie uwierzytelniania usługi RMS za pomocą Portalu Azure | Azure RMS"
description: "Zawiera opis procesu uwierzytelniania przy użyciu biblioteki ADAL"
keywords: uwierzytelnianie, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 06/14/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2680b399-febb-4bd6-b844-ac3d1e69aca4
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f43f5605b1c341d7be618327038d1a86a305a5b
ms.openlocfilehash: cb82f0333ed17ee2994608baa3bbb50d42f19073


---

# Instrukcje: konfigurowanie uwierzytelniania usługi RMS za pomocą Portalu Azure

Uwierzytelnianie w usłudze Azure RMS dla aplikacji z użyciem biblioteki Azure Active Directory Authentication Library (ADAL).

Użycie tej metody wymaga, aby aplikacja zarządzała własnym uwierzytelnianiem OAuth. W przypadku tego podejścia klient RMS wykonuje wywołanie zwrotne określone w aplikacji, gdy jest wymagane uwierzytelnienie.

## Konfigurowanie za pomocą Portalu Azure
Najpierw wykonaj czynności przedstawione w tym przewodniku konfigurowania za pomocą Portalu Azure [Konfigurowanie usługi Azure RMS na potrzeby uwierzytelniania ADAL](adal-auth.md). Skopiuj i zapisz *identyfikator klienta* oraz *identyfikator URI przekierowania* z tego procesu do użycia w przyszłości.

## Przykładowy kod
Poniżej przedstawiono fragment kodu z większego przykładu kodu klientów urządzeń przenośnych umożliwiający włączenie uwierzytelniania opartego na bibliotece Azure ADAL. Aby uzyskać więcej informacji, zobacz pełny przykład w temacie [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)

       /**
       * Instantiates a new rms authentication callback.
       *
       * @param parentActivity the parent activity
       * @throws NoSuchAlgorithmException the no such algorithm exception
       * @throws InvalidKeySpecException the invalid key spec exception
       * @throws UnsupportedEncodingException the unsupported encoding exception
       */

       public MsipcAuthenticationCallback(Activity parentActivity) throws NoSuchAlgorithmException, InvalidKeySpecException, UnsupportedEncodingException
       {
         mParentActivity = parentActivity;
         setADALKeyStore();

         /**
         * Note: Following values of are client_id and redirect_uri are for demo purpose only.
         * Your values will come from the preceeding Azure Portal process.
         */
         mClientId = "com.microsoft.rightsmanagement.sampleapp";
         mRedirectURI = mClientId + "://authorize";
       }


## Tematy pokrewne

- [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)
- [Konfigurowanie usługi Azure RMS na potrzeby uwierzytelniania ADAL](adal-auth.md)



<!--HONumber=Jul16_HO3-->


