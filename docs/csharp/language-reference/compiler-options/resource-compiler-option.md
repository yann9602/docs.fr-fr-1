---
title: "/resource (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/resource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-resource compiler option [C#]"
  - "/resource compiler option [C#]"
  - "-res compiler option [C#]"
  - "/res compiler option [C#]"
  - "res compiler option [C#]"
  - "resource compiler option [C#]"
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /resource (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Insère la ressource spécifiée dans le fichier de sortie.  
  
## Syntaxe  
  
```  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## Arguments  
 `filename`  
 Fichier de ressources .NET Framework que vous voulez incorporer dans le fichier de sortie.  
  
 `identifier` \(facultatif\)  
 Nom logique de la ressource, c'est\-à\-dire le nom utilisé pour charger cette dernière.  La valeur par défaut est le nom du fichier.  
  
 `accessibility-modifier` \(facultatif\)  
 Accessibilité de la ressource : public ou private.  La valeur par défaut est public.  
  
## Notes  
 Utilisez [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) pour lier une ressource à un assembly sans ajouter le fichier de ressources au fichier de sortie.  
  
 Par défaut, les ressources sont publiques dans l'assembly lorsqu'elles sont créées à l'aide du compilateur C\#.  Pour que les ressources soient private, spécifiez `private` comme modificateur d'accessibilité.  Aucune autre accessibilité que `public` ou `private` n'est autorisée.  
  
 Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou dans l'environnement de développement, il est accessible avec des membres dans l'espace de noms <xref:System.Resources>.  Pour plus d'informations, consultez <xref:System.Resources.ResourceManager?displayProperty=fullName>.  Pour toutes les autres ressources, utilisez les méthodes `GetManifestResource`\* dans la classe <xref:System.Reflection.Assembly> pour accéder à la ressource au moment de l'exécution.  
  
 **\/res** est la forme abrégée de **\/resource**.  
  
 L'ordre des ressources dans le fichier de sortie est déterminé par l'ordre spécifié sur la ligne de commande.  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ajoutez un fichier de ressources à votre projet.  
  
2.  Sélectionnez le fichier que vous souhaitez incorporer dans l'**Explorateur de solutions**.  
  
3.  Sélectionnez **Action de génération** pour le fichier dans la fenêtre **Propriétés**.  
  
4.  Définissez **Action de génération** avec **Ressource incorporée**.  
  
 Pour plus d'informations sur la définition de cette option du compilateur par programme, consultez <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## Exemple  
 Compilez `in.cs` et attachez le fichier de ressources `rf.resource` :  
  
```  
csc /resource:rf.resource in.cs  
```  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)