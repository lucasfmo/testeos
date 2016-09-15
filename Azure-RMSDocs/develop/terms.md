---
title: Terminologia | Azure RMS
description: "Definicje terminów specyficznych dla usług Rights Management Services."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: 5779cc10503ad7afe997e031a467021b513fc510


---

# Terminologia

Definicje terminów specyficznych dla usług Rights Management Services.

**Przestarzały algorytm**  
Modalne ustawienie implementujące starszy schemat ochrony zawartości, w szczególności odnoszący się do trybu szyfrowania ECB. W tym zestawie SDK to ustawienie umożliwia wygenerowanie licencji zgodnych z biblioteką MSDRM używaną przez [zestaw AD Rights Management Services SDK](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx).

To ustawienie może spowodować, że aplikacja będzie chronić zawartość w sposób, który nie jest zgodny ze standardami klientów dotyczącymi ochrony zawartości.

To ustawienie uniemożliwi aplikacji korzystanie z rozszerzeń kryptograficznych dodanych do zestawu Microsoft Rights Management SDK 3.0 lub nowszego.

**Format Microsoft Protected File**

Domyślny format pliku (zwany także formatem PFile) dla usług AD RMS, pełniący funkcję standardu dla aplikacji z obsługą usług RMS.

Format PFile jest niewidoczny dla dewelopera aplikacji, ponieważ jest wbudowany w zestaw Microsoft Rights Management SDK 4.2.

 

 






<!--HONumber=Jul16_HO3-->


