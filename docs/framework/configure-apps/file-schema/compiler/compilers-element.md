---
title: "&lt;compilers&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<compilers> (élément)"
  - "éléments de configuration du compilateur, <compilers> (élément)"
  - "compilers (élément)"
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;compilers&gt;, &#233;l&#233;ment
Conteneur d'éléments de configuration de compilateur ; contient zéro, un ou plusieurs éléments [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) .  
  
## Syntaxe  
  
```  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<compiler\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langages.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration\>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<system.codedom\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Spécifie des paramètres de configuration du compilateur pour les fournisseurs de langage disponibles.|  
  
## Notes  
 L'élément [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) contient les paramètres de configuration du compilateur pour les fournisseurs de langage d'un ordinateur.  Chaque élément [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) spécifie les attributs de la configuration du compilateur pour un fournisseur de langages spécifique.  
  
 Le .NET Framework définit les paramètres initiaux du compilateur et du fournisseur de langages dans le fichier de configuration de l'ordinateur \(Machine.config\).  Les développeurs et fournisseurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation de <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName>.  Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> pour énumérer par programme le fournisseur de langages et les paramètres de configuration du compilateur sur un ordinateur.  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'ordinateur et dans le fichier de configuration de l'application.  
  
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
 [Schéma des paramètres du fournisseur de langage et du compilateur](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)   
 [\<compiler\>, élément](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)