---
title: "Troubleshooting: Reading from and Writing to Text Files (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "troubleshooting file I/O"
  - "writing text to files, troubleshooting"
  - "troubleshooting Visual Basic, text files"
  - "I/O [Visual Basic], troubleshooting text files"
  - "writing to files, troubleshooting"
  - "reading text files, troubleshooting"
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Troubleshooting: Reading from and Writing to Text Files (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique aborde les problèmes courants rencontrés lors de l'utilisation des fichiers texte et propose une approche pour chacun d'entre eux.  
  
## Problèmes courants  
 Les problèmes les plus courants rencontrés lors de l'utilisation des fichiers texte concernent les exceptions de sécurité, les encodages de fichiers ou les chemins d'accès incorrects.  
  
### Exceptions de sécurité  
 Une exception <xref:System.Security.SecurityException> est levée lorsqu'une erreur de sécurité se produit.  Cela est souvent est dû au fait que l'utilisateur n'a pas les autorisations nécessaires, ce qui peut être résolu par l'ajout d'autorisations ou l'utilisation des fichiers dans un stockage isolé.  Pour plus d'informations, consultez [Dépannage des exceptions : System.Security.SecurityException](../Topic/Troubleshooting%20Exceptions:%20System.Security.SecurityException.md).  
  
### Encodages de fichiers  
 Les encodages de fichier, également appelés codages de caractères, spécifient comment représenter les caractères lors du traitement de texte.  Les caractères inattendus d'un fichier texte peuvent être dus à un encodage incorrect.  Pour la plupart des fichiers, un encodage peut être préférable à un autre en fonction des caractères de langue qu'il gère, bien qu'Unicode soit généralement préféré.  Pour plus d'informations, consultez [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) et <xref:System.Text.Encoding>.  
  
### Chemins d'accès incorrects  
 Lorsque de l'analyse des chemins d'accès, notamment des chemins d'accès relatifs, il est facile de fournir des données incorrectes.  Vous pouvez résoudre de nombreux problèmes en vérifiant que vous fournissez le chemin d'accès correct.  Pour plus d'informations, consultez [Comment : analyser des chemins d'accès](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)