---
title: "-resource (Options du compilateur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /resource
dev_langs:
- CSharp
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
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
ms.openlocfilehash: fdb7be630300e11c2e63d88bd6add7d229714bfa
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="resource-c-compiler-options"></a>/resource (Options du compilateur C#)
Incorpore la ressource spécifiée dans le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Fichier de ressources .NET Framework que vous voulez incorporer dans le fichier de sortie.  
  
 `identifier` (facultatif)  
 Nom logique de la ressource. Il s’agit du nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier.  
  
 `accessibility-modifier`(facultatif)  
 Accessibilité de la ressource : publique ou privée. La valeur par défaut est « public ».  
  
## <a name="remarks"></a>Remarques  
 Utilisez [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) pour lier une ressource à un assembly sans ajouter le fichier de ressources au fichier de sortie.  
  
 Par défaut, les ressources sont publiques dans l’assembly quand elles sont créées à l’aide du compilateur C#. Pour rendre les ressources privées, spécifiez le modificateur d’accessibilité `private`. Aucune accessibilité autre `public` ou `private` n’est autorisée.  
  
 Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou dans l'environnement de développement, il est accessible à l'aide des membres de l'espace de noms <xref:System.Resources>. Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=fullName>. Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource`* dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l'exécution.  
  
 **/res** est la forme abrégée de **/resource**.  
  
 L’ordre des ressources dans le fichier de sortie est déterminé par l’ordre spécifié sur la ligne de commande.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ajoutez un fichier de ressources à votre projet.  
  
2.  Sélectionnez le fichier que vous souhaitez incorporer dans l’**Explorateur de solutions**.  
  
3.  Sélectionnez **Action de génération** pour le fichier dans la fenêtre **Propriétés**.  
  
4.  Définissez **Action de génération**  sur **Ressource incorporée**.  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Exemple  
 Compilez `in.cs` et attachez le fichier de ressources `rf.resource` :  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)

