---
title: "Comment&#160;: effectuer une conversion entre un codage h&#233;rit&#233; et Unicode (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversions (C#), encodage hérité en encodage Unicode"
  - "chaînes (C#), convertir entre encodages"
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# Comment&#160;: effectuer une conversion entre un codage h&#233;rit&#233; et Unicode (Guide de programmation C#)
En C\#, toutes les chaînes en mémoire sont encodées au format Unicode \(UTF\-16\).  Lorsque vous importez les données d'un support de stockage dans un objet `string`, les données sont converties automatiquement en UTF\-16.  Si les données contiennent uniquement des valeurs ASCII comprises entre 0 et 127, la conversion ne requiert aucune intervention de votre part.  Toutefois, si le texte source contient des valeurs d'octets ASCII étendues \(de 128 à 255\), les caractères étendus seront interprétés par défaut d'après la page de codes actuelle.  Pour spécifier que le texte source doit être interprété d'après une page de codes différente, utilisez la classe <xref:System.Text.Encoding?displayProperty=fullName> comme l'indique l'exemple suivant.  
  
## Exemple  
 L'exemple suivant indique comment convertir un fichier texte encodé au format ASCII 8 bits, en interprétant le texte source d'après la page de codes Windows 737.  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## Voir aussi  
 [Chaînes](../../../csharp/programming-guide/strings/index.md)