---
title: "/link (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "l compiler option [Visual Basic]"
  - "EmbedInteropTypes"
  - "embed interop types [COM Interop]"
  - "-link compiler option [Visual Basic]"
  - "/link compiler option [Visual Basic]"
  - "link compiler option [Visual Basic]"
  - "-l compiler option [Visual Basic]"
  - "/l compiler option [Visual Basic]"
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /link (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Force le compilateur à donner des informations de type COM dans les assemblys spécifiés disponibles pour le projet en cours de compilation.  
  
## Syntaxe  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`fileList`|Obligatoire.  Liste délimitée par des virgules de noms de fichiers d'assembly.  Si le nom de fichier contient un espace, mettez le nom entre guillemets.|  
  
## Notes  
 L'option `/link` vous permet de déployer une application qui a des informations de type incorporées.  L'application peut ensuite utiliser des types dans un assembly de runtime qui implémente les informations de type incorporées sans requérir une référence à l'assembly de runtime.  Si différentes versions de l'assembly de runtime sont publiées, l'application qui contient les informations de type incorporées peut fonctionner avec les différentes versions sans avoir à être recompilée.  Pour obtenir un exemple, consultez [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
 L'utilisation de l'option `/link` est particulièrement utile lorsque vous travaillez avec COM Interop.  Vous pouvez incorporer des types COM afin que votre application ne requière plus un assembly PIA \(Primary Interop Assembly\) sur l'ordinateur cible.  L'option `/link` instruit le compilateur d'incorporer les informations de type COM de l'assembly d'interopérabilité référencé dans le code compilé résultant.  Le type COM est identifié par la valeur CLSID \(GUID\).  Par conséquent, votre application peut s'exécuter sur un ordinateur cible qui a installé les mêmes types COM avec les mêmes valeurs CLSID.  Les applications qui automatisent Microsoft Office sont un bon exemple.  Étant donné que les applications comme Office gardent habituellement la même valeur CLSID dans différentes versions, votre application peut utiliser les types COM référencés tant que le .NET Framework 4 ou version ultérieure est installé sur l'ordinateur cible et que votre application utilise les méthodes, les propriétés ou les  événements inclus dans les types COM référencés.  
  
 L'option `/link` incorpore uniquement des interfaces, des structures et des délégués.  L'incorporation de classes COM n'est pas prise en charge.  
  
> [!NOTE]
>  Lorsque vous créez une instance d'un type COM incorporé dans votre code, vous devez créer l'instance à l'aide de l'interface appropriée.  La tentative de création d'une instance d'un type COM incorporé à l'aide de la coclasse provoque une erreur.  
  
 Pour définir l'option `/link` dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], ajoutez une référence d'assembly et affectez à la propriété `Embed Interop Types` la valeur **true**.  La valeur par défaut de la propriété `Embed Interop Types` est **false**.  
  
 Si vous établissez une liaison à un assembly COM \(Assembly A\) qui lui\-même référence un autre assembly COM \(Assembly B\), vous devez aussi établir une liaison à l'Assembly B si l'un ou l'autre des éléments suivants est vrai :  
  
-   Un type utilisé à partir de l'assembly A hérite d'un type ou implémente une interface à partir de l'assembly B.  
  
-   Un champ, une propriété, un événement ou une méthode dont le type de retour ou de paramètre est issu de l'assembly B est appelé.  
  
 Utilisez [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel se trouvent une ou plusieurs de vos références d'assembly.  
  
 Comme l'option du compilateur [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md), l'option du compilateur `/link` utilise le fichier réponse Vbc.rsp, qui référence les assemblys [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fréquemment utilisés.  Utilisez l'option du compilateur [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) si vous ne souhaitez pas que le compilateur utilise le fichier Vbc.rsp.  
  
 La forme abrégée de `/link` est `/l`.  
  
## Types génériques et imbriqués  
 Les sections suivantes décrivent les limitations de l'utilisation de types génériques dans les applications qui incorporent des types d'interopérabilité.  
  
### Interfaces génériques  
 Les interfaces génériques incorporées depuis un assembly d'interopérabilité ne peuvent pas être utilisées.  L'exemple suivant le démontre.  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### Types ayant des paramètres génériques  
 Les types qui ont un paramètre générique dont le type est incorporé depuis un assembly d'interopérabilité ne peuvent pas être utilisés si ce type est issu d'un assembly externe.  Cette restriction ne s'applique pas aux interfaces.  Par exemple, considérez l'interface <xref:Microsoft.Office.Interop.Excel.Range> définie dans l'assembly <xref:Microsoft.Office.Interop.Excel>.  Si une bibliothèque incorpore des types d'interopérabilité de l'assembly <xref:Microsoft.Office.Interop.Excel> et expose une méthode qui retourne un type générique possédant un paramètre dont le type est l'interface <xref:Microsoft.Office.Interop.Excel.Range>, cette méthode doit retourner une interface générique, comme indiqué dans l'exemple de code suivant.  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 Dans l'exemple suivant, le code client peut appeler la méthode qui retourne l'interface générique <xref:System.Collections.IList> sans erreur.  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## Exemple  
 Le code suivant compile le fichier source `OfficeApp.vb` et référence des assemblys issus de `COMData1.dll` et `COMData2.dll` pour générer `OfficeApp.exe`.  
  
```vb#  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Introduction to COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)