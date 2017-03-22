---
title: /Link (Visual Basic) | Documents Microsoft
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
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e98c855f0a0185e9d1b6682df9fc734e9f1f07bc
ms.lasthandoff: 03/13/2017

---
# <a name="link-visual-basic"></a>/link (Visual Basic)
Entraîne le compilateur à rendre les informations de type COM dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`fileList`|Obligatoire. Liste délimitée par des virgules des noms de fichiers d’assembly. Si le nom de fichier contient un espace, placez le nom entre guillemets.|  
  
## <a name="remarks"></a>Remarques  
 La `/link` option vous permet de déployer une application qui a des informations de type incorporées. L’application peut ensuite utiliser des types dans un assembly de runtime qui implémentent les informations de type incorporées sans requérir une référence à l’assembly de runtime. Si différentes versions de l’assembly de runtime sont publiées, l’application qui contient les informations de type incorporées peut fonctionner avec les différentes versions sans devoir être recompilée. Pour obtenir un exemple, consultez [procédure pas à pas : incorporation de Types provenant d’assemblys gérés](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 À l’aide de la `/link` option est particulièrement utile lorsque vous travaillez avec COM interop. Vous pouvez incorporer des types COM afin que votre application ne requiert plus un assembly interop primaire (PIA) sur l’ordinateur cible. La `/link` option indique au compilateur d’incorporer les informations de type COM de l’assembly PIA référencé dans le code compilé résultant. Le type COM est identifié par la valeur CLSID (GUID). Par conséquent, votre application peut s’exécuter sur un ordinateur cible qui a installé les mêmes types COM avec les mêmes valeurs CLSID. Les applications qui automatisent Microsoft Office sont un bon exemple. Étant donné que les applications comme Office gardent habituellement la même valeur CLSID dans différentes versions, votre application peut utiliser les types COM référencés comme que .NET Framework 4 ou version ultérieure est installé sur l’ordinateur cible et que votre application utilise les méthodes, propriétés ou événements qui sont inclus dans les types COM référencés.  
  
 La `/link` option incorpore uniquement des interfaces, des structures et des délégués. L’incorporation de classes COM n’est pas pris en charge.  
  
> [!NOTE]
>  Lorsque vous créez une instance d’un type COM incorporé dans votre code, vous devez créer l’instance à l’aide de l’interface appropriée. Tente de créer une instance d’un type COM incorporé à l’aide de la coclasse provoque une erreur.  
  
 Pour définir le `/link` option [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], ajoutez une référence d’assembly et affectez le `Embed Interop Types` propriété **true**. La valeur par défaut pour le `Embed Interop Types` propriété **false**.  
  
 Si vous liez à un assembly COM (Assembly A) qui lui-même référence un autre assembly COM (Assembly B), vous devez également lier à l’Assembly B si une des opérations suivantes est vraie :  
  
-   Un type à partir de l’Assembly A hérite d’un type ou implémente une interface à partir de l’Assembly B.  
  
-   Un champ, une propriété, un événement ou une méthode qui a un type de paramètre ou type de retour de l’Assembly B est appelé.  
  
 Utilisez [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel sont trouve une ou plusieurs références d’assembly.  
  
 Comme le [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option du compilateur, la `/link` option du compilateur utilise le fichier réponse Vbc.rsp, qui référence fréquemment utilisés [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblys. Utilisez le [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) option du compilateur si vous ne souhaitez pas que le compilateur utilise le fichier Vbc.rsp.  
  
 La forme abrégée de `/link` est `/l`.  
  
## <a name="generics-and-embedded-types"></a>Types imbriqués et génériques  
 Les sections suivantes décrivent les limitations sur l’utilisation de types génériques dans les applications qui incorporent des types d’interopérabilité.  
  
### <a name="generic-interfaces"></a>Interfaces génériques  
 Impossible d’utiliser des interfaces génériques incorporées depuis un assembly d’interopérabilité. L'exemple suivant le démontre.  
  
 [!code-vb[VbLinkCompiler n °&1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a>Types qui ont des paramètres génériques  
 Types qui ont un paramètre générique dont le type est incorporé depuis un assembly d’interopérabilité ne peut pas être utilisées si ce type est d’un assembly externe. Cette restriction ne s’applique pas aux interfaces. Par exemple, considérez la <xref:Microsoft.Office.Interop.Excel.Range>interface qui est définie dans le <xref:Microsoft.Office.Interop.Excel>assembly.</xref:Microsoft.Office.Interop.Excel> </xref:Microsoft.Office.Interop.Excel.Range> Si une bibliothèque incorpore des types d’interopérabilité de la <xref:Microsoft.Office.Interop.Excel>assembly et expose une méthode qui retourne un type générique qui a un paramètre dont le type est le <xref:Microsoft.Office.Interop.Excel.Range>de l’interface, que méthode doit retourner une interface générique, comme indiqué dans l’exemple de code suivant.</xref:Microsoft.Office.Interop.Excel.Range> </xref:Microsoft.Office.Interop.Excel>  
  
 [!code-vb[VbLinkCompiler n °&2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler n °&3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler n °&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 Dans l’exemple suivant, le code client peut appeler la méthode qui retourne le <xref:System.Collections.IList>interface générique sans erreur.</xref:System.Collections.IList>  
  
 [!code-vb[VbLinkCompiler n °&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a>Exemple  
 Le code suivant compile le fichier source `OfficeApp.vb` et référence des assemblys à partir de `COMData1.dll` et `COMData2.dll` pour produire `OfficeApp.exe`.  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Procédure pas à pas : Incorporation de Types provenant d’assemblys managés](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [/LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Introduction à COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
