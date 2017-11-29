---
title: /codepage (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 609373ed0e58eec86a703f33d48d31e27b0b7e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="codepage-visual-basic"></a>/codepage (Visual Basic)
Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`id`|Obligatoire. Le compilateur utilise la page de codes spécifiée par `id` pour interpréter le codage des fichiers sources.|  
  
## <a name="remarks"></a>Remarques  
 Pour compiler le code source enregistré avec un encodage spécifique, vous pouvez utiliser `/codepage` pour spécifier quelle page de codes doit être utilisée. Le `/codepage` option s’applique à tous les fichiers de code source dans la compilation. Pour plus d’informations, consultez [l’encodage de caractères dans le .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 Le `/codepage` option n’est pas nécessaire si les fichiers de code source ont été enregistrés à l’aide de la page de codes ANSI actuelle, Unicode ou UTF-8 avec une signature. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]enregistre tous les fichiers de code source avec la page de codes ANSI actuelle par défaut, à moins que l’utilisateur spécifie un autre encodage dans la **codage** boîte de dialogue. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]utilise le **codage** boîte de dialogue pour ouvrir des fichiers de code source enregistrés avec une autre page de codes.  
  
> [!NOTE]
>  Le `/codepage` option n’est pas disponible dans le [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] l’environnement de développement, il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
