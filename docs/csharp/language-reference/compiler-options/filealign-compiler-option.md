---
title: -filealign (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /filealign
dev_langs:
- CSharp
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: 14
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
ms.openlocfilehash: 1b13dee0a221bc0b97349be5897a04188304ff16
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="filealign-c-compiler-options"></a>/filealign (Options du compilateur C#)
L’option **/filealign** permet de spécifier la taille des sections de votre fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Valeur qui spécifie la taille des sections dans le fichier de sortie. Les valeurs valides sont 512, 1024, 2048, 4096 et 8192. Ces valeurs sont exprimées en octets.  
  
## <a name="remarks"></a>Remarques  
 Chaque section est alignée sur une limite qui est un multiple de la valeur **/filealign**. Il n’existe aucune valeur fixe par défaut. Si la valeur **/filealign** n’est pas spécifiée, le common language runtime choisit une valeur par défaut au moment de la compilation.  
  
 En spécifiant la taille de la section, vous affectez la taille du fichier de sortie. Il peut être utile de modifier la taille de la section pour les programmes qui sont exécutés sur des appareils de petite taille.  
  
 Utilisez [DUMPBIN](/cpp/build/reference/dumpbin-options) pour afficher des informations sur les sections de votre fichier de sortie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Générer**.  
  
3.  Cliquez sur le bouton **Avancées** .  
  
4.  Modifiez la propriété **Alignement des fichiers**.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

