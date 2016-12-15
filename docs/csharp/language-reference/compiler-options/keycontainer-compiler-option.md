---
title: "/keycontainer (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/keycontainer"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/keycontainer compiler option [C#]"
  - "keycontainer compiler option [C#]"
  - "-keycontainer compiler option [C#]"
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /keycontainer (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie le nom du conteneur de clé de chiffrement.  
  
## Syntaxe  
  
```  
/keycontainer:string  
```  
  
## Arguments  
 `string`  
 Nom du conteneur de clé de nom fort.  
  
## Notes  
 Lorsque l'option **\/keycontainer** est utilisée, le compilateur crée un composant partageable en insérant une clé publique provenant du conteneur spécifié, dans le manifeste d'assembly et en signant l'assembly final avec la clé privée.  Pour générer un fichier de clé, de type Sn \- k `file` sur la ligne de commande. Sn \- I installe la paire de clés dans un conteneur.  
  
 Si vous compilez à l'aide de [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), le nom du fichier de clé est conservé dans le module et incorporé à l'assembly lorsque vous compilez ce module en un assembly à l'aide de [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé \(<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>\) dans le code source de n'importe quel module MSIL \(Microsoft Intermediate Language\).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).  Utilisez [\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) si vous souhaitez que la clé publique soit ajoutée au manifeste d'assembly, mais si vous souhaitez attendre que l'assembly ait été testé pour le signer.  
  
 Pour plus d'informations, consultez [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) et [Temporisation de signature d'un assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
### Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Cette option du compilateur n'est pas disponible dans l'environnement de développement Visual Studio.  
  
 Vous pouvez accéder par programme à cette option du compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## Voir aussi  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)