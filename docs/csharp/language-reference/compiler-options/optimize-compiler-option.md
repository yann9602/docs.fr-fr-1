---
title: -optimize (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a>/optimize (Options du compilateur C#)
L’option **/optimize** active ou désactive les optimisations effectuées par le compilateur pour réduire la taille de votre fichier de sortie et le rendre plus rapide et plus efficace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a>Remarques  
 **/optimize** indique aussi au common language runtime d’optimiser le code au moment de l’exécution.  
  
 Par défaut, les optimisations sont désactivées. Pour activer les optimisations, spécifiez **/optimize+**.  
  
 Quand vous créez un module destiné à être utilisé par un assembly, utilisez les mêmes paramètres **/optimize** que ceux de l’assembly.  
  
 **/o** est la forme abrégée de **/optimize**.  
  
 Il est possible de combiner les options **/optimize** et [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Modifiez la propriété **Optimiser le code**.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Exemple  
 Compilez `t2.cs` et activez les optimisations du compilateur :  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
