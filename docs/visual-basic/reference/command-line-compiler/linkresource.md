---
title: "/linkresource (Visual Basic) | Microsoft Docs"
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
  - "/linkresource compiler option [Visual Basic]"
  - "-linkresource compiler option [Visual Basic]"
  - "linkresource compiler option [Visual Basic]"
  - "/linkres compiler option [Visual Basic]"
  - "linkres compiler option [Visual Basic]"
  - "-linkres compiler option [Visual Basic]"
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /linkresource (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Crée un lien vers une ressource managée.  
  
## Syntaxe  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## Arguments  
 `filename`  
 Obligatoire.  Fichier de ressources à lier à l'assembly.  Si le nom de fichier contient un espace, mettez le nom entre guillemets \(" "\).  
  
 `identifier`  
 Facultatif.  Nom logique de la ressource.  Nom utilisé pour charger la ressource.  La valeur par défaut est le nom du fichier.  Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste d'assembly, par exemple :`/linkres:filename.res,myname.res,public`.  Par défaut, `filename` est public dans l'assembly.  
  
## Notes  
 L'option `/linkresource` n'incorpore pas le fichier de ressources dans le fichier de sortie ; utilisez plutôt l'option `/resource` pour cela.  
  
 L'option  `/linkresource` nécessite une option `/target` différente de `/target:module`.  
  
 Si `filename` est un fichier de ressources [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] créé, par exemple, par le [Resgen.exe \(Resource File Generator\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou dans l'environnement de développement, il est accessible à l'aide de membres de l'espace de noms <xref:System.Resources>.  \(Pour plus d'informations, consultez <xref:System.Resources.ResourceManager>\). Pour accéder à toutes les autres ressources au moment de l'exécution, utilisez les méthodes qui commencent par `GetManifestResource` dans la classe <xref:System.Reflection.Assembly>.  
  
 Le nom de fichier peut être de n'importe quel format de fichier.  Par exemple, vous pouvez décider d'intégrer une DLL native dans l'assembly. Ainsi, elle pourra être installée dans le Global Assembly Cache et sera accessible depuis le code managé de l'assembly.  
  
 La forme abrégée de `/linkresource` est `/linkres`.  
  
> [!NOTE]
>  L'option `/linkresource` n'est pas disponible depuis l'environnement de développement Visual Studio. Elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## Exemple  
 Le code suivant compile `In.vb` et le lie au fichier de ressources `Rf.resource` :  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [\/resource](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)