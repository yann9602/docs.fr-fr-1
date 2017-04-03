---
title: "##pragma checksum (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5daf71faea5736036e9e3e0178e84ea03c314ff6
ms.lasthandoff: 03/13/2017

---
# <a name="pragma-checksum-c-reference"></a>##pragma checksum (référence C#)
Génère des sommes de contrôle pour les fichiers sources afin de faciliter le débogage des pages [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Paramètres  
 `"filename"`  
 Nom du fichier dont les modifications ou les mises à jour doivent faire l’objet d’une surveillance.  
  
 `"{guid}"`  
 Identificateur global unique (GUID) du fichier.  
  
 `"checksum_bytes"`  
 Chaîne de chiffres hexadécimaux représentant les octets de la somme de contrôle. Doit être un nombre pair de chiffres hexadécimaux. S’il y a un nombre impair de chiffres, un avertissement est généré au moment de la compilation et la directive est ignorée.  
  
## <a name="remarks"></a>Notes  
 Le débogueur Visual Studio utilise une somme de contrôle pour s’assurer de toujours trouver la bonne source. Le compilateur calcule la somme de contrôle pour un fichier source, puis envoie la sortie vers le fichier de base de données du programme (PDB). Le débogueur utilise ensuite le fichier PDB à comparer avec la somme de contrôle qu’il calcule pour le fichier source.  
  
 Cette solution n’est pas possible pour les projets [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)], car la somme de contrôle est calculée pour le fichier source généré, au lieu du fichier .aspx. Pour résoudre ce problème, `#pragma checksum` fournit une prise en charge de la somme de contrôle pour les pages [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].  
  
 Quand vous créez un projet [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] dans [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)], le fichier source généré contient une somme de contrôle pour le fichier .aspx, à partir duquel la source est générée. Le compilateur écrit ensuite ces informations dans le fichier PDB.  
  
 Si le compilateur ne rencontre aucune directive `#pragma checksum` dans le fichier, il calcule la somme de contrôle et écrit la valeur dans le fichier PDB.  
  
## <a name="example"></a>Exemple  
  
```  
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)
