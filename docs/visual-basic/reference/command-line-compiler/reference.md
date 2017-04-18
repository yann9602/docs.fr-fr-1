---
title: Reference (Visual Basic) | Documents Microsoft
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
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
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
ms.openlocfilehash: 12344dba82131d6be2c32127de287a6e9e3efa39
ms.lasthandoff: 03/13/2017

---
# <a name="reference-visual-basic"></a>/reference (Visual Basic)
Entraîne le compilateur à rendre les informations de type dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`fileList`|Obligatoire. Liste délimitée par des virgules des noms de fichiers d’assembly. Si le nom de fichier contient un espace, placez le nom entre guillemets.|  
  
## <a name="remarks"></a>Remarques  
 Les fichiers que vous importez doivent contenir des métadonnées de l’assembly. Seuls les types publics sont visibles en dehors de l’assembly. Le [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option importe des métadonnées à partir d’un module.  
  
 Si vous référencez un assembly (Assembly A) qui lui-même référence un autre assembly (Assembly B), vous devez référencer l’Assembly B si :  
  
-   Un type à partir de l’Assembly A hérite d’un type ou implémente une interface à partir de l’Assembly B.  
  
-   Un champ, une propriété, un événement ou une méthode qui a un type de paramètre ou type de retour de l’Assembly B est appelé.  
  
 Utilisez [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel sont trouve une ou plusieurs références d’assembly.  
  
 Le compilateur reconnaisse un type dans un assembly (pas un module), il doit être forcé à résoudre le type. Un exemple de comment vous pouvez faire cela consiste à définir une instance du type. Autres méthodes sont disponibles pour résoudre les noms de types dans un assembly pour le compilateur. Par exemple, si vous héritez d’un type dans un assembly, le nom de type puis devienne connu du compilateur.  
  
 Le fichier réponse Vbc.rsp, qui référence couramment utilisés [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblys, est utilisé par défaut. Utilisez `/noconfig` si vous ne souhaitez pas que le compilateur utilise Vbc.rsp.  
  
 La forme abrégée de `/reference` est `/r`.  
  
## <a name="example"></a>Exemple  
 La suivant code compile le fichier source je`nput.vb` et référence des assemblys de M`etad1.dll` et M`etad2.dll` pour produire O`ut.exe`.  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
