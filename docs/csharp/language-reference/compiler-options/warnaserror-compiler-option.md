---
title: -warnaserror (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /warnaserror
dev_langs:
- CSharp
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 15
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
ms.openlocfilehash: df29fd760e0e4a002f1b5078d85370a74f322e23
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="warnaserror-c-compiler-options"></a>/warnaserror (Options du compilateur C#)
L’option **/warnaserror+** considère tous les avertissements comme des erreurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## <a name="remarks"></a>Remarques  
 Les messages qui d’ordinaire auraient été signalés comme des avertissements s’affichent en tant qu’erreurs, et le processus de génération est arrêté (aucun fichier de sortie n’est généré).  
  
 Comme **/warnaserror** est activé par défaut, les avertissements n’empêchent pas la génération d’un fichier de sortie. Du fait de **/warnaserror**, qui est identique à **/warnaserror+**, les avertissements sont considérés comme des erreurs.  
  
 Le cas échéant, si vous voulez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules qui liste les numéros d’avertissement à considérer comme des erreurs.  
  
 Utilisez [/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) pour spécifier le niveau des avertissements que le compilateur doit afficher. Utilisez [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) pour désactiver certains avertissements.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Modifiez la propriété **Considérer les avertissements comme des erreurs**.  
  
     Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.  
  
## <a name="example"></a>Exemple  
 Compilez `in.cs` et faites en sorte que le compilateur n’affiche aucun avertissement :  
  
```console  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

