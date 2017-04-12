---
title: /subsystemversion (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bc9ea6a844fae7f98315e5d3557fdf306f467dd5
ms.lasthandoff: 03/13/2017

---
# <a name="subsystemversion-visual-basic"></a>/subsystemversion (Visual Basic)
Spécifie la version minimale du sous-système sur lequel le fichier exécutable généré peut s’exécuter, en déterminant les versions de Windows sur lequel le fichier exécutable peut s’exécuter. En règle générale, cette option garantit que le fichier exécutable peut tirer parti des fonctionnalités de sécurité qui ne sont pas disponibles avec les versions antérieures de Windows.  
  
> [!NOTE]
>  Pour spécifier le sous-système lui-même, utilisez la [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Paramètres  
 `major.minor`  
 La version minimale requise du sous-système, comme cela est exprimé dans une notation par points pour les versions majeures et mineures. Par exemple, vous pouvez spécifier qu’une application ne peut pas s’exécuter sur un système d’exploitation qui est antérieure à Windows 7 si vous définissez la valeur de cette option sur 6.01, comme décrit dans le tableau plus loin dans cette rubrique. Vous devez spécifier les valeurs de `major` et `minor` en tant qu’entiers.  
  
 Zéros de début le `minor` version ne modifiez pas la version, mais que faire de zéros de fin. Par exemple, 6.1 et 6.01 font référence à la même version, mais 6.10 fait référence à une version différente. Nous vous recommandons d’exprimer la version secondaire à deux chiffres pour éviter toute confusion.  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant répertorie les versions de sous-système commun de Windows.  
  
|Version Windows|Version du sous-système|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|6.02|  
  
## <a name="default-values"></a>Valeurs par défaut  
 La valeur par défaut de la **/subsystemversion** option du compilateur dépend des conditions dans la liste suivante :  
  
-   La valeur par défaut est 6.02 si toutes les options du compilateur dans la liste suivante sont définie :  
  
    -   [/ target : appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [/ target : winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [/Platform:ARM](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   La valeur par défaut est 6,00 si vous utilisez MSBuild, vous ciblez [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)], et vous n’avez pas défini les options du compilateur qui ont été spécifiées plus haut dans cette liste.  
  
-   La valeur par défaut est 4.00 si aucune des conditions précédentes est true.  
  
## <a name="setting-this-option"></a>Définition de cette option  
 Pour définir le **/subsystemversion** option du compilateur dans Visual Studio, vous devez ouvrir le fichier .vbproj et spécifiez une valeur pour le `SubsystemVersion` propriété dans le XML de MSBuild. Vous ne pouvez pas définir cette option dans l’IDE de Visual Studio. Pour plus d’informations, consultez « Valeurs par défaut » plus haut dans cette rubrique ou [propriétés communes des projets MSBuild](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties).  
  

  
## <a name="see-also"></a>Voir aussi  
[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)

[Propriétés MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-properties)

