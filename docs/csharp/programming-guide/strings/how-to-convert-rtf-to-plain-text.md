---
title: "Comment&#160;: convertir du RTF en texte brut (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "chaînes (C#), convertir à partir de RTF"
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: convertir du RTF en texte brut (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le format RTF \(Rich Text Format\) est un format de document développé par Microsoft à la fin des années 1980 pour permettre l'échange de documents entre les systèmes d'exploitation.  Microsoft Word et WordPad peuvent lire et écrire des documents RTF.  Dans le .NET Framework, vous pouvez utiliser le contrôle <xref:System.Windows.Forms.RichTextBox> pour créer un traitement de texte qui prend en charge le format RTF et permet à un utilisateur d'appliquer une mise en forme de type WYSIWYG au texte.  
  
 Vous pouvez également utiliser le contrôle <xref:System.Windows.Forms.RichTextBox> pour supprimer par programme les codes de formatage RTF d'un document et le convertir en texte brut.  Vous n'avez pas besoin d'incorporer le contrôle dans un Windows Form pour effectuer ce type d'opération.  
  
### Pour utiliser le contrôle RichTextBox dans un projet  
  
1.  Ajoutez une référence à System.Windows.Forms.dll.  
  
2.  Ajoutez une directive using pour l'espace de noms `System.Windows.Forms` \(facultatif\).  
  
## Exemple  
 L'exemple suivant convertit un fichier RTF d'exemple au texte brut.  Le fichier contient le format RTF \(comme les informations de police\), quatre caractères Unicode, et quatre caractères étendus ASCII.  L'exemple de code ouvre le fichier, passe son contenu à <xref:System.Windows.Forms.RichTextBox> que RTF, récupère le contenu sous forme de texte, affiche le texte dans <xref:System.Windows.Forms.MessageBox>, et affiche le texte à un fichier au format UTF\-8.  
  
 `MessageBox` et le fichier de sortie contiennent le texte suivant :  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
  
```  
  
 [!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]  
  
 Les caractères RTF sont encodés en huit bits.  Toutefois, les utilisateurs peuvent spécifier des caractères Unicode en plus de les caractères étendus ASCII des pages de codes spécifiées.  Étant donné que la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> est de type [chaîne](../../../csharp/language-reference/keywords/string.md), les caractères sont encodés au format Unicode UTF\-16.  Les caractères étendus ASCII et les caractères Unicode du document RTF source sont encodés correctement dans la sortie de texte.  
  
 Si vous utilisez la méthode <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> pour écrire le texte sur un disque, le texte sera encodé au format UTF\-8 \(sans marque d'ordre d'octet\).  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox?displayProperty=fullName>   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)