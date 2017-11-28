---
title: "-codepage (Options du compilateur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37f40312f1218b8e666eae7cb2de6c768ee32108
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="codepage-c-compiler-options"></a>/codepage (Options du compilateur C#)
Cette option spécifie la page de codes à utiliser pendant la compilation si la page exigée n’est pas la page de codes par défaut actuelle du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
 `id`  
 Identificateur de la page de codes à utiliser pour tous les fichiers de code source de la compilation.  
  
## <a name="remarks"></a>Remarques  
 Si vous compilez un ou plusieurs fichiers de code source n’ayant pas été créés pour utiliser la page de codes par défaut de votre ordinateur, vous pouvez utiliser l’option **/codepage** pour spécifier la page de codes à utiliser. **/codepage** s’applique à tous les fichiers de code source inclus dans votre compilation.  
  
 Il n’est pas nécessaire d’utiliser **/codepage** si les fichiers de code source ont été créés avec la même page de codes que celle en vigueur sur votre ordinateur ou bien avec le format de codage UNICODE ou UTF-8.  
  
 Pour plus d’informations sur la façon de savoir quelles pages de codes sont prises en charge sur votre système, consultez [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371).  
  
 Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
