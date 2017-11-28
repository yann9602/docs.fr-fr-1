---
title: -nostdlib (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad3ca7775512623de43c7fe6b7fe1cf481ccca87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
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
