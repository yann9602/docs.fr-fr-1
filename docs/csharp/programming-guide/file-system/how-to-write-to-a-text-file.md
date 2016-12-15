---
title: "Comment&#160;: &#233;crire dans un fichier texte (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TextWriter.WriteLine"
  - "StreamWriter.Close"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fichiers (C#), fichiers texte"
  - "texte, écrire dans les fichiers (C#)"
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: &#233;crire dans un fichier texte (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ces exemples montrent différentes manières d'écrire du texte dans un fichier.  Les deux premiers exemples utilisent des méthodes pratiques statiques sur la classe <xref:System.IO.File?displayProperty=fullName> pour écrire chaque élément de tout IEnumerable\<string\> et une chaîne dans un fichier texte.  L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier.  Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.  
  
 Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.  Vous pouvez également utiliser la fonctionnalité C\# [d'interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).  
  
## Exemple  
 [!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.  Vous pouvez également utiliser la fonctionnalité C\# [d'interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le fichier existe déjà et est en lecture seule.  
  
-   Le nom du chemin d'accès peut s'avérer trop long.  
  
-   Le disque est peut\-être plein.  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [Exemple : enregistrer une collection dans un emplacement de stockage d'application](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)