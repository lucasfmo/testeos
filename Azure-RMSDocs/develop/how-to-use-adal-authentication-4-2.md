---
title: "Konfiguráció az RMS-hitelesítéshez az Azure-portállal | Azure RMS"
description: "Az ADAL hitelesítési folyamatának ismertetése"
keywords: "hitelesítés, RMS, ADAL"
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

# Útmutató: Konfiguráció az RMS-hitelesítéshez az Azure-portállal

Hitelesítés az Azure RMS-sel az ADAL-hitelesítést (Azure Active Directory Authentication Library) használó alkalmazás esetén.

Ennek a megközelítésnek az előfeltétele, hogy az alkalmazás kezelje az OAuth-hitelesítést. Ezzel a megközelítéssel az RMS-ügyfél egy, az alkalmazás által meghatározott visszahívást intéz, ha hitelesítésre van szükség.

## Konfigurálás az Azure-portálon
Elsőként tekintse meg ezt az útmutatót az Azure-portálon való konfigurálásról: [Az Azure RMS konfigurálása ADAL-hitelesítéshez](adal-auth.md). A folyamat során másolja ki és mentse el az *ügyfél-azonosítót* és *átirányítási URI-t* későbbi használatra.

## Kódminta
Alább megtekinthet egy Azure ADAL-t engedélyező kódtöredéket a mobil ügyfélalkalmazás kódjából. További információért tekintse meg a teljes mintát itt: [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)

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


## Kapcsolódó témakörök

- [MSIPCSampleApp](https://github.com/AzureAD/rms-sdk-ui-for-android/tree/master/samples/MsipcSampleApp)
- [Az Azure RMS beállítása az ADAL-hitelesítéshez](adal-auth.md)



<!--HONumber=Jul16_HO3-->


