---
title: "/platform (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/platform"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "platform compiler option [C#]"
  - "-platform compiler option [C#]"
  - "/platform compiler option [C#]"
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
caps.handback.revision: 46
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /platform (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie quelle version du common language runtime \(CLR\) peut exécuter l'assembly.  
  
## Syntaxe  
  
```  
/platform:string  
```  
  
#### Paramètres  
 `string`  
 anycpu, anycpu32bitpreferred, ARM, x64, x86, or Itanium \(valeur par défaut\).  
  
## Notes  
  
-   **anycpu** \(valeur par défaut\) compile votre assembly pour qu'il soit exécuté sur n'importe quelle plateforme.  Votre application s'exécute en tant que processus 64 bits autant que possible et revient à 32 bits uniquement lorsque ce mode est disponible.  
  
-   **anycpu32bitpreferred** compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme.  Votre application s'exécute en mode 32 bits sur les systèmes qui prennent en charge 64 bits et aux applications 32 bits.  Vous pouvez spécifier cette option uniquement pour les projets qui ciblent .NET Framework 4,5.  
  
-   **ARM** compile l'assembly pour s'exécuter sur un ordinateur qui possède un processeur gigaoctets \(ARM\) d'ordinateur Advanced RISC.  
  
-   **x64** compile votre assembly pour qu'il soit exécuté par le Common Language Runtime 64 bits sur un ordinateur qui prend en charge le jeu d'instructions AMD64 ou EM64T.  
  
-   **x86** compile votre assembly en vue d'une exécution par le common language runtime 32 bits compatible x86.  
  
-   **Itanium** compile votre assembly en vue d'une exécution par le common language runtime 64 bits sur un ordinateur à processeur Itanium.  
  
 Sur un système d'exploitation Windows 64 bits :  
  
-   Les assemblys compilés avec **\/platform:x86** s'exécutent sur le CLR 32\-bits qui s'exécute sous WOW64.  
  
-   Une DLL compilée avec **\/platform:anycpu** s'exécute sur le même CLR que le processus dans lequel elle est chargée.  
  
-   Les fichiers exécutables qui sont compilés avec **\/platform:anycpu** s'exécutent sur le CLR 64\-bits.  
  
-   les fichiers exécutables compilés avec **\/platform:anycpu32bitpreferred** exécutent sur le CLR 32 bits ;  
  
 La définition de **anycpu32bitpreferred** est valide uniquement pour les fichiers \(.EXE\) exécutables, et il requiert .NET Framework 4,5.  
  
 Pour plus d'informations sur le développement d'une application à exécuter sur un système d'exploitation 64 bits Windows, consultez [Applications 64 bits](../Topic/64-bit%20Applications.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Remplacez la propriété **Plateforme cible** et, pour les projets qui cible le .NET Framework 4,5, activez ou désactivez la case à cocher **Préférer 32 bits**.  
  
 **Remarque**  
 **\/platform** n'est pas disponible dans l'environnement de développement en Visual C\# Express.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## Exemple  
 L'exemple suivant indique comment utiliser l'option **\/platform** pour spécifier que l'application ne doit être exécutée que par le CLR 64 bits sur un système d'exploitation Windows 64 bits pour Itanium.  
  
```  
csc /platform:anycpu filename.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)