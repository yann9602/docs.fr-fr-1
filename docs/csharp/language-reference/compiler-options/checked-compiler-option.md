---
title: "-checked (Options du compilateur C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6cfc54c2dbd3e14d874d7684fdc75a972260cc3
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="checked-c-compiler-options"></a>/checked (Options du compilateur C#)
L’option **/checked** spécifie si une instruction arithmétique entière qui produit une valeur en dehors de la plage du type de données, et qui n’est pas dans la portée d’un mot clé [checked](../../../csharp/language-reference/keywords/checked.md) ou [unchecked](../../../csharp/language-reference/keywords/unchecked.md), doit provoquer une exception au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/checked[+ | -]  
```  
  
## <a name="remarks"></a>Notes  
 Une instruction arithmétique entière qui est dans la portée d’un mot clé `checked` ou `unchecked` n’est pas soumise à l’effet de l’option **/checked**.  
  
 Si une instruction arithmétique entière qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked` produit une valeur en dehors de la plage du type de données, et que **/checked+** (**/checked**) est utilisé dans la compilation, cette instruction provoque une exception au moment de l’exécution. Si **/checked-** est utilisé dans la compilation, cette instruction ne provoque pas d’exception au moment de l’exécution.  
  
 La valeur par défaut pour cette option est **/checked-**. Vous pouvez notamment employer **/checked-** pour générer des applications de grande taille. Des outils automatisés sont parfois utilisés pour créer ces applications et peuvent affecter automatiquement + à **/checked**. Vous pouvez remplacer l’option globale par défaut de l’outil en spécifiant **/checked-**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet. Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](https://docs.microsoft.com/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancées** .  
  
4.  Modifiez la propriété **Vérifier les dépassements de capacité arithmétiques positifs et négatifs**.  
  
 Pour accéder à cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Exemple  
 La commande suivante compile `t2.cs`. L’utilisation de `/checked` dans la commande spécifie que toute instruction arithmétique entière dans le fichier qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked`, et qui produit une valeur en dehors de la plage du type de données, provoque une exception au moment de l’exécution.  
  
```console  
csc t2.cs /checked  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Présentation du Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)
