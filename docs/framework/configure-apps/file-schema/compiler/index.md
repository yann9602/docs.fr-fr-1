---
title: "Sch&#233;ma des param&#232;tres du fournisseur de langage et du compilateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "éléments de configuration du compilateur"
  - "éléments de configuration du compilateur, schéma"
  - "paramètres de configuration du compilateur"
  - "paramètres de configuration du compilateur, schéma"
  - "schéma de configuration (.NET Framework), paramètres du compilateur"
  - "paramètres de configuration (.NET Framework), compilateurs"
  - "fournisseurs de langages"
  - "fournisseurs de langages, schéma des paramètres"
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Sch&#233;ma des param&#232;tres du fournisseur de langage et du compilateur
Les paramètres du compilateur et du fournisseur de langage spécifient des éléments de configuration du compilateur pour les fournisseurs de langage disponibles.  Chaque élément de configuration de compilateur spécifie le nom du type de fournisseur de code, les paramètres du compilateur, les noms des langages pris en charge et les extensions de fichier prises en charge.  
  
 Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l'ordinateur \(Machine.config\).  Les développeurs et fournisseurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation de <xref:System.CodeDom.Compiler.CodeDomProvider>.  Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> pour énumérer par programme le fournisseur de langages et les paramètres de configuration du compilateur sur un ordinateur.  
  
 [\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [\<compilateurs\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Spécifie des paramètres de configuration du compilateur pour les fournisseurs de langage disponibles.|  
|[\<compilateurs\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Conteneur d'éléments de configuration de compilateur ; contient zéro, un ou plusieurs éléments [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) .|  
|[\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langages.|  
  
## Exemple  
 L'exemple suivant illustre un élément de configuration de compilateur classique :  
  
```  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler  
          language="c#;cs;csharp"  
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""  
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.CodeDom.Compiler.CompilerInfo>   
 <xref:System.CodeDom.Compiler.CodeDomProvider>   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<compiler\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)