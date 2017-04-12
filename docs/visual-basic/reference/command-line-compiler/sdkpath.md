---
title: /sdkpath | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
dev_langs:
- VB
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
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
ms.openlocfilehash: 3584daa49bca699f022a1afd34e3d450b8442060
ms.lasthandoff: 03/13/2017

---
# <a name="sdkpath"></a>/sdkpath
Spécifie l'emplacement de Mscorlib.dll et de Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Le répertoire contenant les versions de Mscorlib.dll et de Microsoft.VisualBasic.dll à utiliser pour la compilation. Ce chemin d’accès n’est pas vérifié jusqu'à ce qu’il est chargé. Placez le nom de répertoire entre guillemets (« ») s’il contient un espace.  
  
## <a name="remarks"></a>Notes  
 Cette option indique à le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur de charger les fichiers Mscorlib.dll et de Microsoft.VisualBasic.dll à partir d’un emplacement non définis par défaut. Le `/sdkpath` option a été conçue pour être utilisée avec [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). Le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] utilise différentes versions de ces bibliothèques d’assistance pour éviter l’utilisation de types et de fonctionnalités de langue introuvables sur les périphériques.  
  
> [!NOTE]
>  La `/sdkpath` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande. Le `/sdkpath` option est définie lorsque un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet smart device est chargé.  
  
 Vous pouvez spécifier que le compilateur doit compiler sans référence à la bibliothèque Runtime Visual Basic à l’aide de la `/vbruntime` option du compilateur. Pour plus d’informations, consultez [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Myfile.vb` avec la [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], l’utilisation des versions de Mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut de le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] sur le lecteur C. En général, vous utilisez la version la plus récente de la [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)   
 [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
