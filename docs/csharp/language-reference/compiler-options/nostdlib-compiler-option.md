---
title: -nostdlib (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nostdlib
dev_langs:
- CSharp
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1d500e2e55ab3117aa674e11d6cdd25703035879
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="nostdlib-c-compiler-options"></a>/nostdlib (Options du compilateur C#)
**/nostdlib** empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms System tout entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>Remarques  
 Utilisez cette option si vous souhaitez définir ou créer vos propres objets et espace de noms System.  
  
 Si vous ne spécifiez pas **/nostdlib**, mscorlib.dll est importé dans votre programme (ce qui équivaut à spécifier **/nostdlib-**). Les options **/nostdlib** et **/nostdlib+**sont équivalentes.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer** .  
  
3.  Cliquez sur le bouton **Avancées** .  
  
4.  Modifiez la propriété **Ne pas référencer mscorlib.dll** .  
  
 Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)

