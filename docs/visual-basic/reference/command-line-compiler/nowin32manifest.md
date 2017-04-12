---
title: /nowin32manifest (Visual Basic) | Documents Microsoft
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
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
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
ms.openlocfilehash: feac0ca5008925711c12bdb54ed95d4b3d79c1ef
ms.lasthandoff: 03/13/2017

---
# <a name="nowin32manifest-visual-basic"></a>/nowin32manifest (Visual Basic)
Indique au compilateur de ne pas incorporer de manifeste d'application dans le fichier exécutable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/nowin32manifest  
```  
  
## <a name="remarks"></a>Remarques  
 Lorsque cette option est utilisée, l’application sera soumis à la virtualisation sur Windows Vista, sauf si vous fournissez un manifeste d’application dans un fichier de ressources Win32 ou au cours d’une étape de génération ultérieure. Pour plus d’informations sur la virtualisation, consultez [déploiement ClickOnce sur Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Pour plus d’informations sur la création de manifestes, consultez [/win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Page Application, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)
