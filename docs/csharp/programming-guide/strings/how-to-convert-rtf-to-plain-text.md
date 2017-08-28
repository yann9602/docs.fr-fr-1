---
title: Guide pratique pour convertir du RTF en texte brut (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting from RTF
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e4c7b48467f3b260526c604fa3a36fc5d80374e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-rtf-to-plain-text-c-programming-guide"></a>Guide pratique pour convertir du RTF en texte brut (Guide de programmation C#)
Le format RTF (Rich Text Format) est un format de document développé par Microsoft à la fin des années 1980 pour permettre l’échange de documents entre les systèmes d’exploitation. Microsoft Word et WordPad peuvent tous les deux lire et écrire des documents RTF. Dans le .NET Framework, vous pouvez utiliser le contrôle <xref:System.Windows.Forms.RichTextBox> pour créer un traitement de texte qui prend en charge le format RTF et permet à un utilisateur d’appliquer une mise en forme de type WYSIWYG au texte.  
  
 Vous pouvez également utiliser le contrôle <xref:System.Windows.Forms.RichTextBox> pour supprimer par programmation les codes de mise en forme RTF d’un document et le convertir en texte brut. Vous n’avez pas besoin d’incorporer le contrôle dans un Windows Form pour effectuer ce type d’opération.  
  
### <a name="to-use-the-richtextbox-control-in-a-project"></a>Pour utiliser le contrôle RichTextBox dans un projet  
  
1.  Ajoutez une référence à System.Windows.Forms.dll.  
  
2.  Ajoutez une directive using pour l’espace de noms `System.Windows.Forms` (facultatif).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant convertit un exemple de fichier RTF en texte brut. Le fichier contient la mise en forme RTF (comme les informations de police), quatre caractères Unicode et quatre caractères ASCII étendus. L’exemple de code ouvre le fichier, transmet son contenu à un <xref:System.Windows.Forms.RichTextBox> au format RTF, récupère le contenu sous forme de texte, affiche le texte dans un <xref:System.Windows.Forms.MessageBox>, puis affiche le texte dans un fichier au format UTF-8.  
  
 `MessageBox` et le fichier de sortie contiennent le texte suivant :  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
```  
  
 [!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]  
  
 Les caractères RTF sont encodés dans huit bits. Toutefois, les utilisateurs peuvent spécifier des caractères Unicode en plus de les caractères étendus ASCII des pages de codes spécifiées. Étant donné que la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> est de type [string](../../../csharp/language-reference/keywords/string.md), les caractères sont encodés au format Unicode UTF-16. Les caractères ASCII étendus et les caractères Unicode du document RTF source sont encodés correctement dans la sortie de texte.  
  
 Si vous utilisez la méthode <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> pour écrire le texte sur le disque, le texte doit être encodé au format UTF-8 (sans marque d’ordre d’octet).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.RichTextBox?displayProperty=fullName>   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)

