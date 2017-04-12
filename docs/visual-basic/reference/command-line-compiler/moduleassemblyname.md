---
title: /moduleassemblyname | Documents Microsoft
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
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
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
ms.openlocfilehash: f6b042b26ad866f177158562653c91f4f7527c04
ms.lasthandoff: 03/13/2017

---
# <a name="moduleassemblyname"></a>/moduleassemblyname
Spécifie le nom de l’assembly dont ce module doit faire partie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`assembly_name`|Le nom de ce module fera partie de l’assembly.|  
  
## <a name="remarks"></a>Remarques  
 Le compilateur traite les `/moduleassemblyname` option uniquement si la `/target:module` option a été spécifiée. Cela entraîne le compilateur à créer un module. Le module créé par le compilateur est valide uniquement pour l’assembly spécifié avec la `/moduleassemblyname` option. Si vous placez le module dans un assembly différent, les erreurs d’exécution seront produit.  
  
 La `/moduleassemblyname` option est uniquement requise lorsque les conditions suivantes sont remplies :  
  
-   Un type de données dans le module a besoin d’accéder à un `Friend` type dans un assembly référencé.  
  
-   L’assembly référencé a accordé l’accès d’assembly friend à l’assembly dans lequel le module sera généré.  
  
 Pour plus d’informations sur la création d’un module, consultez [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md). Pour plus d’informations sur les assemblys friend, consultez [assemblys Friend](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
> [!NOTE]
>  La `/moduleassemblyname` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir d’une invite de commandes.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : générer un Assembly multifichier](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5)   
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/ main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Assemblys friend](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
