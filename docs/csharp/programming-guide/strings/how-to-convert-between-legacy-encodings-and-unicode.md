---
title: "Guide pratique pour effectuer une conversion entre un codage hérité et Unicode (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], legacy to unicode encoding
- strings [C#], converting between encodings
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a016f4ab7de25eec408243cb9b467f9255556bba
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a>Guide pratique pour effectuer une conversion entre un codage hérité et Unicode (Guide de programmation C#)
En C#, toutes les chaînes en mémoire sont encodées au format Unicode (UTF-16). Quand vous importez les données d’un support de stockage dans un objet `string`, les données sont automatiquement converties en UTF-16. Si les données contiennent uniquement des valeurs ASCII comprises entre 0 et 127, la conversion ne nécessite aucune intervention supplémentaire de votre part. Toutefois, si le texte source contient des valeurs d’octets ASCII étendus (de 128 à 255), les caractères étendus sont interprétés par défaut en fonction de la page de codes actuelle. Pour spécifier que le texte source doit être interprété en fonction d’une page de codes différente, utilisez la classe <xref:System.Text.Encoding?displayProperty=fullName>, comme l’indique l’exemple suivant.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant indique comment convertir un fichier texte encodé au format ASCII 8’bits, en interprétant le texte source en fonction de la page de codes Windows 737.  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes](../../../csharp/programming-guide/strings/index.md)

