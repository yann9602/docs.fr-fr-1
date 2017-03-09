---
title: "/platform (Visual Basic) | Microsoft Docs"
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
  - "platform compiler option [Visual Basic]"
  - "/platform compiler option [Visual Basic]"
  - "-platform compiler option [Visual Basic]"
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 34
---
# /platform (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie la version de plateforme du CLR \(Common Language Runtime\) qui peut exécuter le fichier de sortie.  
  
## Syntaxe  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`x86`|Compile votre assembly pour qu'il soit exécuté par le CLR 32 bits x86.|  
|`x64`|Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d'instructions AMD64 ou EM64T.|  
|`Itanium`|Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur doté d'un processeur Itanium.|  
|`arm`|Compile votre assembly pour qu'il s'exécute sur un ordinateur doté d'un processeur ARM \(Advanced RISC Machine\).|  
|`anycpu`|Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme.  L'application s'exécutera en tant qu'application 32 bits sur les versions 32 bits de Windows et en tant qu'application 64 bits sur les versions 64 bits de Windows.  Cet indicateur est la valeur par défaut.|  
|`anycpu32bitpreferred`|Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme.  L'application s'exécutera en tant qu'application 32 bits sur les versions 32 et 64 bits de Windows.  Cet indicateur n'est valide que pour les fichiers exécutables \(.EXE\) et nécessite [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net-v45-md.md)].|  
  
## Notes  
 Utilisez l'option `/platform` pour spécifier le type de processeur ciblé par le fichier de sortie.  
  
 En général, les assemblys .NET Framework écrits en Visual Basic s'exécutent de la même façon, quelle que soit la plateforme.  Cependant, dans certains cas, leur comportement peut varier d'une plateforme à une autre.  Voici les cas les plus courants :  
  
-   Structures contenant des membres qui changent de taille selon la plateforme, comme un type pointeur.  
  
-   Opération arithmétique de pointeur qui inclut des tailles constantes.  
  
-   Appel de plateforme incorrect ou déclarations COM qui utilisent `Integer` pour des handles au lieu de <xref:System.IntPtr>.  
  
-   Cast de <xref:System.IntPtr> en `Integer`.  
  
-   Utilisation d'un appel de plateforme ou de COM interop avec des composants qui n'existent pas sur toutes les plateformes.  
  
 L'option **\/platform** permet de limiter certains problèmes si vous avez émis des hypothèses quant à l'architecture sur laquelle votre code sera exécuté.  Plus précisément :  
  
-   Si vous décidez de cibler une plateforme 64 bits et que l'application est exécutée sur un ordinateur 32 bits, le message d'erreur intervient bien plus tôt et est davantage axé sur le problème que sur l'erreur qui se produit quand ce commutateur n'est pas utilisé.  
  
-   Si vous définissez l'indicateur `x86` au niveau de l'option et que l'application est par la suite exécutée sur un ordinateur 64 bits, l'application s'exécutera dans le sous\-système WOW au lieu de s'exécuter en mode natif.  
  
 Sur un système d'exploitation Windows 64 bits :  
  
-   Les assemblys compilés avec `/platform:x86` s'exécutent sur le CLR 32 bits fonctionnant sous WOW64.  
  
-   Les fichiers exécutables compilés avec `/platform:anycpu` s'exécutent sur le CLR 64 bits.  
  
-   Une DLL compilée avec `/platform:anycpu` s'exécute sur le même CLR que le processus dans lequel elle est chargée.  
  
-   Les fichiers exécutables compilés avec `/platform:anycpu32bitpreferred` s'exécutent sur le CLR 32 bits.  
  
 Pour plus d'informations sur le développement d'une application destinée à s'exécuter sur une version 64 bits de Windows, consultez [Applications 64 bits](../Topic/64-bit%20Applications.md).  
  
### Pour définir \/platform dans l'IDE de Visual Studio  
  
1.  Dans l'**Explorateur de solutions**, choisissez le projet, ouvrez le menu **Projet**, puis cliquez sur **Propriétés**.  
  
     Pour plus d'informations, consultez [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/fr-fr/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Sous l'onglet **Compiler**, cochez ou décochez la case **Préférer 32 bits** ou, dans la liste **Unité centrale cible**, choisissez une valeur.  
  
     Pour plus d'informations, consultez [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic).  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'option de compilateur `/platform`.  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## Voir aussi  
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)