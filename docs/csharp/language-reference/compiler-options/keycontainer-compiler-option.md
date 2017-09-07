---
title: -keycontainer (Options du compilateur C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keycontainer
dev_langs:
- CSharp
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
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
ms.openlocfilehash: 5d27fa0b80ca6df15394ad1fda149377cac41a8b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="keycontainer-c-compiler-options"></a>/keycontainer (Options du compilateur C#)
Spécifie le nom du conteneur de la clé de chiffrement.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Nom du conteneur de clé de nom fort.  
  
## <a name="remarks"></a>Remarques  
 Quand l’option **/keycontainer** est utilisée, le compilateur crée un composant partageable en insérant une clé publique provenant du conteneur spécifié dans le manifeste d’assembly et en signant l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez sn -k `file` sur la ligne de commande. sn -i installe la paire de clés dans un conteneur.  
  
 Si vous compilez avec [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly quand vous compilez ce module dans un assembly avec [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>) dans le code source de n'importe quel module MSIL (Microsoft Intermediate Language).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Utilisez [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) si vous voulez ajouter la clé publique au manifeste d’assembly, mais que vous voulez différer la signature de l’assembly tant qu’il n’a pas été testé.  
  
 Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](https://msdn.microsoft.com/library/xwb8f617) et [Différer la signature d’un assembly](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Cette option de compilateur n’est pas disponible dans l'environnement de développement Visual Studio.  
  
 Vous pouvez accéder par programmation à cette option de compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

