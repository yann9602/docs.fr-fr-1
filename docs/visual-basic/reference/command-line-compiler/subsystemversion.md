---
title: "-subsystemversion (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
helpviewer_keywords: 
  - "/subsystemversion (option du compilateur Visual Basic)"
  - "-subsystemversion (option du compilateur Visual Basic)"
  - "subsystemversion (option du compilateur Visual Basic)"
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# /subsystemversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

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
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>Valeurs par défaut  
 La valeur par défaut de la **/subsystemversion** option du compilateur dépend des conditions dans la liste suivante :  
  
-   La valeur par défaut est 6.02 si toutes les options du compilateur dans la liste suivante sont définie :  
  
    -   [/ target : appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [/ target : winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)  
  
    -   [/Platform:ARM](../../../visual-basic/reference/command-line-compiler/platform.md)  
  
-   La valeur par défaut est 6,00 si vous utilisez MSBuild, vous ciblez [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net-v45-md.md)], et vous n’avez pas défini les options du compilateur qui ont été spécifiées plus haut dans cette liste.  
  
-   La valeur par défaut est 4.00 si aucune des conditions précédentes est true.  
  
## <a name="setting-this-option"></a>Définition de cette option  
 Pour définir le **/subsystemversion** option du compilateur dans Visual Studio, vous devez ouvrir le fichier .vbproj et spécifiez une valeur pour le `SubsystemVersion` propriété dans le XML de MSBuild. Vous ne pouvez pas définir cette option dans l’IDE de Visual Studio. Pour plus d’informations, consultez « Valeurs par défaut » plus haut dans cette rubrique ou [Propriétés communes des projets MSBuild](/visual-studio/msbuild/common-msbuild-project-properties).  
  

  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
 [propriétés MSBuild](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/ee3538c5-0d7d-4c18-a1d7-edf460cd1c8a/locales/en-US)