---
title: /win32icon | Documents Microsoft
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
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
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
ms.openlocfilehash: 110a3861d6628dc2c3fb251aaa31762fb94f04c9
ms.lasthandoff: 03/13/2017

---
# <a name="win32icon"></a>/win32icon
Insère un fichier .ico dans le fichier de sortie. Ce fichier .ico représente le fichier de sortie dans **Explorateur de fichiers**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`filename`|Le fichier .ico à ajouter à votre fichier de sortie. Placez le nom de fichier entre guillemets (« ») s’il contient un espace.|  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez créer un fichier .ico avec le compilateur de ressource Windows (RC) Microsoft. Le compilateur de ressources est appelé lorsque vous compilez un programme Visual C++ ; un fichier .ico est créé à partir du fichier .rc. Le `/win32icon` et `/win32resource` options s’excluent mutuellement.  
  
 Consultez [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fichier de ressources, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fichier de ressources. Consultez la page [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) pour importer un fichier .res.  
  
|Pour définir /win32icon dans l’IDE de Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Application** .<br />3.  Modifiez la valeur dans la **icône** boîte.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et attache un fichier .ico, `Rf.ico`.  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
