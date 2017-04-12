---
title: / keycontainer | Documents Microsoft
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
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
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
ms.openlocfilehash: 68fa09edce5c0c9af143197f9379d5a46afab52e
ms.lasthandoff: 03/13/2017

---
# <a name="keycontainer"></a>/keycontainer
Spécifie un nom de conteneur de clé pour une paire de clés afin d'attribuer un nom fort à un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`container`|Obligatoire. Fichier conteneur qui contient la clé. Placez le nom de fichier entre guillemets (" ») si le nom contient un espace.|  
  
## <a name="remarks"></a>Remarques  
 Le compilateur crée le composant partageable en insérant une clé publique dans le manifeste d’assembly et en signant l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez `sn -k``file` à la ligne de commande. La `-i` option installe la paire de clés dans un conteneur. Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).  
  
 Si vous compilez avec `/target:module`, le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly qui est créé lorsque vous compilez un assembly avec [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyNameAttribute>) dans le code source de n’importe quel module Microsoft intermediate language (MSIL).</xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Utilisez [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) si vous souhaitez obtenir un assembly partiellement signé.  
  
 Consultez la page [création et utilisation d’assemblys](https://msdn.microsoft.com/library/xwb8f617) pour plus d’informations sur la signature d’un assembly.  
  
> [!NOTE]
>  La `/keycontainer` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile le fichier source `Input.vb` et spécifie un conteneur de clé.  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/ keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
