---
title: "#pragma checksum (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#pragma checksum"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma checksum (C#)"
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# #pragma checksum (R&#233;f&#233;rence C#)
Génère des checksums pour les fichiers sources afin d'aider au débogage de pages [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)].  
  
## Syntaxe  
  
```  
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### Paramètres  
 `"filename"`  
 Nom du fichier à surveiller pour toute modification ou mise à jour.  
  
 `"{guid}"`  
 GUID \(Identificateur global unique\) du fichier.  
  
 `"checksum_bytes"`  
 Chaîne de chiffres hexadécimaux représentant les octets du checksum.  Doit être un nombre pair de chiffres hexadécimaux.  Un nombre impair de chiffres engendre un avertissement de compilation et la directive est ignorée.  
  
## Notes  
 Le débogueur Visual Studio utilise un checksum pour s'assurer de toujours trouver la bonne source.  Le compilateur calcule le checksum d'un fichier source, puis transmet la sortie au fichier de base de données du programme \(PDB\).  Le débogueur utilise ensuite le PDB pour effectuer une comparaison avec le checksum calculé pour le fichier source.  
  
 Cette solution ne fonctionne pas avec les projets [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)], le checksum calculé ne portant que sur le fichier source généré, plutôt que sur le fichier .aspx.  Pour corriger ce problème, `#pragma checksum` prend en charge le checksum des pages [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)].  
  
 Lorsque vous créez un projet [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] dans [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)], le fichier source généré contient un checksum du fichier .aspx à partir duquel la source est générée.  Le compilateur écrit ensuite cette information dans le fichier PDB.  
  
 Si le compilateur ne rencontre aucune directive `#pragma checksum` dans le fichier, il calcule le checksum et en écrit la valeur dans le fichier PDB.  
  
## Exemple  
  
```  
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)