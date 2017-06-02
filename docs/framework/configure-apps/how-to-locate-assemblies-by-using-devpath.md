---
title: "Comment&#160;: localiser des assemblys &#224; l&#39;aide de DEVPATH | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "configuration d'applications .NET Framework, assemblys"
  - "fichiers app.config, emplacements des assemblys"
  - "fichiers de configuration de l'application, spécifier l'emplacement d'un assembly"
  - "assemblys (.NET Framework), emplacement"
  - "DEVPATH"
  - "rechercher des assemblys"
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Comment&#160;: localiser des assemblys &#224; l&#39;aide de DEVPATH
Les développeurs peuvent rencontrer la nécessité de s'assurer qu'un assembly partagé qu'ils sont en train de construire fonctionne correctement avec des applications multiples.  Plutôt que de placer systématiquement l'assembly dans le Global Assembly Cache pendant le développement, le programmeur pourra créer une variable d'environnement DEVPATH pointant vers le répertoire de sortie de l'assembly.  
  
 Par exemple, supposons que vous soyez en train de créer un assembly partagé appelé MySharedAssembly et que le répertoire de sortie soit C:\\MySharedAssembly\\Debug.  Il vous suffit de placer C:\\MySharedAssembly\\Debug dans la variable DEVPATH.  Vous devez ensuite spécifier l'élément [\<developmentMode\>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) dans le fichier de configuration machine.  Cet élément indique au Common Language Runtime d'utiliser DEVPATH pour localiser les assemblys.  
  
 L'assembly partagé doit pouvoir être retrouvé par le runtime.  Pour spécifier un répertoire privé pour résoudre des références d'assembly, utilisez les éléments [\<codeBase\>, élément](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) ou [\<probing\>, élément](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) dans un fichier de configuration, comme décrit dans [Spécification de l'emplacement d'un assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  Vous pouvez également placer l'assembly dans un sous\-répertoire du répertoire de l'application.  Pour plus d'informations, consultez [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
>  Il s'agit d'une caractéristique avancée, prévue uniquement pour le développement.  
  
 L'exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d'environnement DEVPATH.  
  
## Exemple  
  
```  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 La valeur par défaut de ce paramètre est False.  
  
> [!NOTE]
>  Utilisez ce paramètre au moment du développement uniquement.  Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH.  Il utilise simplement le premier assembly qu'il trouve.  
  
## Voir aussi  
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/fr-fr/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)