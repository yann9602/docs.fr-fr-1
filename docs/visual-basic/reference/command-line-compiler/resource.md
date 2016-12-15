---
title: "/resource (Visual Basic) | Microsoft Docs"
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
  - "/resource compiler option [Visual Basic]"
  - "-resource compiler option [Visual Basic]"
  - "/res compiler option [Visual Basic]"
  - "res compiler option [Visual Basic]"
  - "-res compiler option [Visual Basic]"
  - "resource compiler option [Visual Basic]"
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /resource (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Incorpore une ressource managée dans un assembly.  
  
## Syntaxe  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`filename`|Obligatoire.  Nom du fichier de ressources à incorporer dans le fichier de sortie.  Par défaut, `filename` est public dans l'assembly.  Mettez le nom de fichier entre guillemets \(" "\) s'il contient un espace.|  
|`identifier`|Facultatif.  Nom logique de la ressource, c'est\-à\-dire le nom utilisé pour charger cette dernière.  La valeur par défaut est le nom du fichier.  Vous pouvez éventuellement spécifier si la ressource est publique ou privée dans le manifeste de l'assembly ; par exemple : `/res:``filename.res`,`myname.res`,`public`|  
  
## Notes  
 Utilisez `/linkresource` pour lier une ressource à un assembly sans placer le fichier de ressources dans le fichier de sortie.  
  
 Si `filename` est un fichier de ressources [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] créé, par exemple, par le [Resgen.exe \(Resource File Generator\)](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou dans l'environnement de développement, il est accessible avec des membres de l'espace de noms <xref:System.Resources> \(pour plus d'informations, consultez <xref:System.Resources.ResourceManager>\).  Pour accéder à toutes les autres ressources au moment de l'exécution, utilisez l'une des méthodes suivantes : <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 La forme abrégée de `/resource`  est `/res`.  
  
 Pour plus d'informations sur la façon de définir `/resource` dans l'IDE de Visual Studio, voir [Gestion des ressources d'une application \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet).  
  
## Exemple  
 Le code suivant compile `In.vb` et le joint au fichier de ressources `Rf.resource`.  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)   
 [\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)