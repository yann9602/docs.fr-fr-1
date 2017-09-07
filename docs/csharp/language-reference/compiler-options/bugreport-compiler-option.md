---
title: "-bugreport (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /bugreport
dev_langs:
- CSharp
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: 20
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
ms.openlocfilehash: ccfea1aa7e51ad013418f61bc4478034c9a5d830
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="bugreport-c-compiler-options"></a>/bugreport (Options du compilateur C#)
Spécifie que les informations de débogage doivent être placées dans un fichier pour une future analyse.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/bugreport:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Nom du fichier qui doit contenir votre rapport de bogues.  
  
## <a name="remarks"></a>Remarques  
 L’option **/bugreport** spécifie que les informations suivantes doivent être placées dans `file` :  
  
-   Une copie de tous les fichiers de code source de la compilation.  
  
-   Une liste des options du compilateur utilisées dans la compilation.  
  
-   Les informations de version concernant votre compilateur, votre runtime et votre système d’exploitation.  
  
-   Les assemblys et modules référencés, enregistrés sous la forme de chiffres hexadécimaux, sauf les assemblys qui sont fournis avec le .NET Framework et le SDK.  
  
-   Les résultats de la compilation, le cas échéant.  
  
-   Une description du problème, qui vous sera demandée.  
  
-   Une description de vos suggestions de résolution du problème, qui vous sera demandée.  
  
 Si cette option est utilisée avec **/errorreport:prompt** ou **/errorreport:send**, les informations figurant dans le fichier seront envoyées à Microsoft Corporation.  
  
 Étant donné qu’une copie de tous les fichiers de code source sera placée dans `file`, vous souhaiterez peut-être reproduire l’erreur de code suspecte dans le programme le plus court possible.  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
 Notez que le contenu du fichier généré expose le code source, ce qui pourrait entraîner une divulgation d’informations non voulue.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [-errorreport (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

