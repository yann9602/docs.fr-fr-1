---
title: -lib (Options du compilateur C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /lib
dev_langs:
- CSharp
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 27bcca456a7a5c884c33de6429e06c94afc9536a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="lib-c-compiler-options"></a>/lib (Options du compilateur C#)
L’option **/lib** spécifie l’emplacement des assemblys référencés au moyen de l’option [/reference (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Arguments  
 `dir1`  
 Un répertoire dans lequel le compilateur doit effectuer la recherche si un assembly référencé ne se trouve pas dans le répertoire de travail actuel (le répertoire à partir duquel vous appelez le compilateur) ou dans le répertoire système du common language runtime.  
  
 `dir2`  
 Un ou plusieurs répertoires supplémentaires où rechercher des références d’assembly. Séparez les noms des répertoires supplémentaires par une virgule, sans espace.  
  
## <a name="remarks"></a>Remarques  
 Le compilateur recherche les références d’assembly qui ne sont pas complètes dans l’ordre suivant :  
  
1.  Répertoire de travail actuel. Il s’agit du répertoire à partir duquel le compilateur est appelé.  
  
2.  Répertoire système du common language runtime.  
  
3.  Répertoires spécifiés par **/lib**.  
  
4.  Répertoires spécifiés par la variable d’environnement LIB.  
  
 Utilisez **/reference** pour spécifier une référence d’assembly.  
  
 **/lib** est additif. Si vous le spécifiez plusieurs fois, il effectue un ajout aux valeurs précédentes.  
  
 Au lieu d’utiliser **/lib**, vous pouvez copier dans le répertoire de travail les assemblys nécessaires. De cette façon, vous passez simplement le nom de l’assembly à **/reference**. Vous pouvez ensuite supprimer les assemblys du répertoire de travail. Comme le chemin de l’assembly dépendant n’est pas spécifié dans le manifeste de l’assembly, l’application peut être démarrée sur l’ordinateur cible, et recherche et utilise l’assembly dans le Global Assembly Cache.  
  
 Le fait que le compilateur puisse référencer l’assembly n’implique pas que le common language runtime soit en mesure de rechercher et charger l’assembly au moment de l’exécution. Consultez [Méthode de localisation des assemblys par le runtime](../../../framework/deployment/how-the-runtime-locates-assemblies.md) pour plus d’informations sur la façon dont le runtime recherche des assemblys référencés.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet.  
  
2.  Cliquez sur la page de propriétés **Chemin aux références**.  
  
3.  Modifiez le contenu de la zone de liste.  
  
 Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## <a name="example"></a>Exemple  
 Compilez t2.cs pour créer un fichier .exe. Le compilateur recherche les références d’assembly dans le répertoire de travail et dans le répertoire racine du lecteur C.  
  
```console  
csc /lib:c:\ /reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
