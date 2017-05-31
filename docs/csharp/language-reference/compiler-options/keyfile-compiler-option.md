---
title: "-keyfile (Options du compilateur C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keyfile
dev_langs:
- CSharp
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 4f9ccbfe7126aac3214ccf08015353eec0490cd4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="keyfile-c-compiler-options"></a>/keyfile (Options du compilateur C#)
Spécifie le nom du fichier contenant la clé de chiffrement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|----------|----------------|  
|`file`|Nom du fichier contenant la clé de nom fort.|  
  
## <a name="remarks"></a>Remarques  
 Quand cette option est utilisée, le compilateur insère la clé publique du fichier spécifié dans le manifeste d'assembly, puis signe l'assembly final avec la clé privée. Pour générer un fichier de clé, tapez sn -k `file` sur la ligne de commande.  
  
 Si vous compilez avec **/target:module**, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly avec [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Utilisez [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) si vous voulez obtenir un assembly partiellement signé.  
  
 Si /keyfile et /keycontainer sont spécifiés (par option de ligne de commande ou par attribut personnalisé) dans la même compilation, le compilateur essaie d’abord d’utiliser le conteneur de clé. Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé. Si le compilateur ne trouve pas le conteneur de clé, il essaie d’utiliser le fichier spécifié avec /keyfile. En cas de réussite, l'assembly est signé avec les informations du fichier de clé et les informations sur la clé sont installées dans le conteneur de clé (semblable à sn -i) de sorte qu'à la compilation suivante, le conteneur de clé est valide.  
  
 Notez qu’un fichier de clé peut contenir uniquement la clé publique.  
  
 Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](https://msdn.microsoft.com/library/xwb8f617) et [Différer la signature d’un assembly](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la page **Propriétés** du projet.  
  
2.  Cliquez sur la page de propriétés **Signature**.  
  
3.  Modifiez la propriété **Choisir un fichier de clé de nom fort**.  
  
 Vous pouvez accéder par programmation à cette option de compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
