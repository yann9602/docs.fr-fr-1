---
title: /filealign | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
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
ms.openlocfilehash: 18d5c3e327e2e41f4786eda6c3e981125f87389d
ms.lasthandoff: 03/13/2017

---
# <a name="filealign"></a>/filealign
Spécifie où les sections du fichier de sortie doivent être alignées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Obligatoire. Une valeur qui spécifie l’alignement des sections dans le fichier de sortie. Les valeurs valides sont 512, 1024, 2048, 4096 et 8192. Ces valeurs sont exprimées en octets.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser la `/filealign` option pour spécifier l’alignement des sections dans votre fichier de sortie. Les sections sont les blocs de mémoire contiguë dans un fichier exécutable Portable (PE) qui contient du code ou des données. La `/filealign` option vous permet de compiler votre application avec un alignement non standard ; la plupart des développeurs n’avez pas besoin d’utiliser cette option.  
  
 Chaque section est alignée sur une limite qui est un multiple de la `/filealign` valeur. Il n’existe aucune valeur par défaut fixe. Si `/filealign` n’est pas spécifié, le compilateur sélectionne la valeur par défaut au moment de la compilation.  
  
 En spécifiant la taille de la section, vous pouvez modifier la taille du fichier de sortie. Modification de la taille de la section peut être utile pour les programmes qui seront exécuteront sur les périphériques de petite taille.  
  
> [!NOTE]
>  La `/filealign` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
