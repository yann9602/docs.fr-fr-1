---
title: /Platform (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: 34
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6216ee056bc9dd8dd7dfd95b9d5a031880209370
ms.lasthandoff: 03/13/2017

---
# <a name="platform-visual-basic"></a>/platform (Visual Basic)
Spécifie la version de plateforme du CLR (Common Language Runtime) qui peut exécuter le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`x86`|Compile votre assembly pour qu'il soit exécuté par le CLR 32 bits x86.|  
|`x64`|Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d'instructions AMD64 ou EM64T.|  
|`Itanium`|Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur doté d'un processeur Itanium.|  
|`arm`|Compile votre assembly pour qu'il s'exécute sur un ordinateur doté d'un processeur ARM (Advanced RISC Machine).|  
|`anycpu`|Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme. L'application s'exécutera en tant qu'application 32 bits sur les versions 32 bits de Windows et en tant qu'application 64 bits sur les versions 64 bits de Windows. Cet indicateur est la valeur par défaut.|  
|`anycpu32bitpreferred`|Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme. L'application s'exécutera en tant qu'application 32 bits sur les versions 32 et 64 bits de Windows. Cet indicateur n'est valide que pour les fichiers exécutables (.EXE) et nécessite [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)].|  
  
## <a name="remarks"></a>Remarques  
 Utilisez l'option `/platform` pour spécifier le type de processeur ciblé par le fichier de sortie.  
  
 En général, les assemblys .NET Framework écrits en Visual Basic s'exécutent de la même façon, quelle que soit la plateforme. Cependant, dans certains cas, leur comportement peut varier d'une plateforme à une autre. Voici les cas les plus courants :  
  
-   Structures contenant des membres qui changent de taille selon la plateforme, comme un type pointeur.  
  
-   Opération arithmétique de pointeur qui inclut des tailles constantes.  
  
-   Plateforme incorrect appeler ou déclarations COM qui utilisent `Integer` pour les handles au lieu de <xref:System.IntPtr>.</xref:System.IntPtr>  
  
-   Conversion de <xref:System.IntPtr>à `Integer`.</xref:System.IntPtr>  
  
-   Utilisation d'un appel de plateforme ou de COM interop avec des composants qui n'existent pas sur toutes les plateformes.  
  
 Le **/platform** option permet de limiter certains problèmes si vous savez que vous avez fait des hypothèses sur l’architecture de votre code sera exécuté. Plus précisément :  
  
-   Si vous décidez de cibler une plateforme 64 bits et que l'application est exécutée sur un ordinateur 32 bits, le message d'erreur intervient bien plus tôt et est davantage axé sur le problème que sur l'erreur qui se produit quand ce commutateur n'est pas utilisé.  
  
-   Si vous définissez l'indicateur `x86` au niveau de l'option et que l'application est par la suite exécutée sur un ordinateur 64 bits, l'application s'exécutera dans le sous-système WOW au lieu de s'exécuter en mode natif.  
  
 Sur un système d'exploitation Windows 64 bits :  
  
-   Les assemblys compilés avec `/platform:x86` s'exécutent sur le CLR 32 bits fonctionnant sous WOW64.  
  
-   Les fichiers exécutables compilés avec `/platform:anycpu` s'exécutent sur le CLR 64 bits.  
  
-   Une DLL compilée avec `/platform:anycpu` s'exécute sur le même CLR que le processus dans lequel elle est chargée.  
  
-   Les fichiers exécutables compilés avec `/platform:anycpu32bitpreferred` s'exécutent sur le CLR 32 bits.  
  
 Pour plus d’informations sur le développement d’une application s’exécute sur une version 64 bits de Windows, consultez la page [Applications 64 bits](https://msdn.microsoft.com/library/ms241064).  
  
### <a name="to-set-platform-in-the-visual-studio-ide"></a>Pour définir /platform dans l'IDE de Visual Studio  
  
1.  Dans **l’Explorateur de solutions**, choisissez le projet, ouvrez le **projet** menu, puis sur **propriétés**.  
  
     Pour plus d’informations, consultez [NIB : gestion des propriétés de projet avec le Concepteur de projet](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Sur le **compiler** onglet, activez ou désactivez le **préférer 32 bits** case à cocher, ou, dans le **UC cible** , choisissez une valeur.  
  
     Pour plus d’informations, consultez [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'option de compilateur `/platform`.  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [/target (Visual Basic)](target.md)   
 [Compilateur de ligne de commande de Visual Basic](index.md)   
 [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
