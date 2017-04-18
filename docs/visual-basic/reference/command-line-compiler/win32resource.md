---
title: /win32resource | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
dev_langs:
- VB
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: 13
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
ms.openlocfilehash: 37902590d5a05d7fdb2a521f3c3de2ad88c2c502
ms.lasthandoff: 03/13/2017

---
# <a name="win32resource"></a>/win32resource
Insère un fichier de ressources Win32 dans le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Le nom du fichier de ressources à ajouter à votre fichier de sortie. Placez le nom de fichier entre guillemets (« ») s’il contient un espace.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez créer un fichier de ressources Win32 avec le compilateur de ressource Windows (RC) Microsoft.  
  
 Une ressource Win32 peut contenir de version ou des informations d’image bitmap (icône) qui vous aide à identifier votre application dans **Explorateur de fichiers**. Si vous ne spécifiez pas `/win32resource`, le compilateur génère des informations de version en fonction de la version d’assembly. Le `/win32resource` et `/win32icon` options s’excluent mutuellement.  
  
 Consultez [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fichier de ressources, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fichier de ressources.  
  
> [!NOTE]
>  La `/win32resource` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et attache un fichier de ressources Win32 `Rf.res`:  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
