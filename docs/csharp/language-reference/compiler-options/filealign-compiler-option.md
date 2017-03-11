---
title: "/filealign (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/filealign"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/alignment compiler option [C#]"
  - "filealign compiler option [C#]"
  - "-filealign compiler option [C#]"
  - "/sections compiler option [C#]"
  - "alignment compiler option [C#]"
  - "sections compiler option [C#]"
  - "-sections compiler option [C#]"
  - "/filealign compiler option [C#]"
  - "file sharing [C#]"
  - "-alignment compiler option [C#]"
  - "section alignment [C#]"
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# /filealign (C# Compiler Options)
L'option **\/filealign** permet de spécifier la taille des sections dans le fichier de sortie.  
  
## Syntaxe  
  
```  
/filealign:number  
```  
  
## Arguments  
 `number`  
 Valeur spécifiant la taille des sections du fichier de sortie.  Les valeurs valides sont 512, 1024, 2048, 4096 et 8192.  Il s'agit de valeurs en octets.  
  
## Notes  
 Chaque section est alignée sur une limite qui est un multiple de la valeur **\/filealign**.  Il n'y a pas de valeur par défaut fixe.  Si vous ne spécifiez pas l'option **\/filealign**, le Common Language Runtime choisit la valeur par défaut au moment de la compilation.  
  
 En spécifiant la taille de la section, vous déterminez aussi la taille du fichier de sortie.  Il est parfois utile de modifier la taille de section pour les programmes appelés à s'exécuter sur des appareils plus petits.  
  
 Utilisez [DUMPBIN](/visual-cpp/build/reference/dumpbin-options) pour obtenir plus d'informations sur les sections de votre fichier de sortie.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancé**.  
  
4.  Modifiez la propriété **Alignement des fichiers**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)