---
title: "File Encodings (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "character encodings"
  - "files, encoding"
  - "Unicode, file encoding"
  - "file encoding"
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# File Encodings (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les encodages de fichier, également appelés codages de caractères, spécifient comment représenter les caractères lors du traitement de texte.  Un encodage peut être préférable à un autre compte tenu des caractères de langage qu'il gère ou non, bien qu'Unicode soit préféré habituellement.  
  
 Lors de la lecture ou de l'écriture de fichiers, les encodages incorrects de fichiers correspondants peuvent causer des exceptions ou des résultats inexacts.  
  
## Types d'encodages  
 Unicode est l'encodage par défaut pour utiliser les fichiers.  Unicode est une norme d'encodage de caractères mondial qui utilise des valeurs de code 16 bits pour représenter tous les caractères utilisés dans l'informatique moderne, y compris les symboles techniques et les caractères spéciaux utilisés dans la publication.  
  
 Les normes d'encodage de caractères antérieurs étaient composées de jeux de caractères traditionnels, tels que le jeu de caractères ANSI Windows qui utilise des valeurs de code de 8 bits, ou des combinaisons de valeurs de 8 bits, pour représenter les caractères utilisés dans un langage ou une zone géographique précis.  
  
## Classe d'encodage  
 La classe <xref:System.Text.Encoding> représente un encodage de caractères.  Ce tableau répertorie le type d'encodage disponible et décrit chacun d'entre eux.  
  
|||  
|-|-|  
|Nom|Description|  
|<xref:System.Text.ASCIIEncoding>|Représente un encodage de caractère ASCII de caractères Unicode.|  
|<xref:System.Text.UnicodeEncoding>|Représente un encodage UTF\-16 de caractères Unicode.|  
|<xref:System.Text.UTF32Encoding>|Représente un encodage UTF\-32 de caractères Unicode.|  
|<xref:System.Text.UTF7Encoding>|Représente un encodage UTF\-7 de caractères Unicode.|  
|<xref:System.Text.UTF8Encoding>|Représente un encodage UTF\-8 de caractères Unicode.|  
  
## Voir aussi  
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)