---
title: "&lt;system.codedom&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.codedom> (élément)"
  - "éléments de configuration du compilateur, <system.codedom> (élément)"
  - "system.codedom (élément)"
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;system.codedom&gt;, &#233;l&#233;ment
Spécifie des paramètres de configuration du compilateur pour les fournisseurs de langage disponibles.  
  
## Syntaxe  
  
```  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<compilateurs\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Conteneur d'éléments de configuration de compilateur ; contient zéro, un ou plusieurs éléments [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) .|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<Configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Notes  
  
## .NET Framework version 2.0  
 L'élément [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) contient des paramètres de configuration de compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut installés avec le .NET Framework, tels que le <xref:Microsoft.CSharp.CSharpCodeProvider> et le <xref:Microsoft.VisualBasic.VBCodeProvider>.  L'élément [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) contient zéro ou plus élément [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).  Chaque élément [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) spécifie les attributs de la configuration du compilateur pour un fournisseur de langages spécifique.  
  
 Les développeurs et fournisseurs de compilateurs peuvent ajouter des paramètres de configuration au fichier de configuration machine \(Machine.config\) pour une nouvelle implémentation de <xref:System.CodeDom.Compiler.CodeDomProvider>.  Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration de compilateur sur un ordinateur.  
  
> [!NOTE]
>  Dans les versions 1.0 et 1.1 du .NET Framework, les fournisseurs de langages par défaut fournis par le .NET Framework sont identifiés dans l'élément [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md).  Dans le .NET Framework version 2.0, les fournisseurs de langages par défaut ne sont pas identifiés dans l'élément [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md), mais peuvent être énumérés à l'aide de la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A>.  
  
## Versions 1.0 et 1.1 du .NET Framework  
 L'élément [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) contient les paramètres de configuration du compilateur pour les fournisseurs de langages d'un ordinateur.  L'élément [\<compilers\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) contient zéro ou plus élément [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) .  Chaque élément [\<compiler\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) spécifie les attributs de la configuration du compilateur pour un fournisseur de langages spécifique.  
  
 Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l'ordinateur \(Machine.config\).  Les développeurs et fournisseurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation de <xref:System.CodeDom.Compiler.CodeDomProvider>.  Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> pour énumérer par programme le fournisseur de langages et les paramètres de configuration du compilateur sur un ordinateur.  
  
## Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration de l'ordinateur et dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant illustre une configuration de compilateur classique :  
  
```  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
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