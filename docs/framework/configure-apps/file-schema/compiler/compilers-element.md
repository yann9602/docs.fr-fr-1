---
title: "&lt;compilateurs&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bea78fe5086a73e4cc588973764ac9bbef2fadc4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompilersgt-element"></a>&lt;compilateurs&gt; élément
Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).  
  
 \<configuration>  
\<System.CodeDom >  
\<compilateurs > élément  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration>, élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|[\<System.CodeDom > élément](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.|  
  
## <a name="remarks"></a>Remarques  
 Le [ \<compilateurs >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) élément contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur. Chaque [ \<compilateur >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langage spécifique.  
  
 Le .NET Framework définit les paramètres du fournisseur de langage du compilateur initial dans le fichier de configuration de l’ordinateur (Machine.config). Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>. Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé dans le fichier de configuration machine et le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre un élément de configuration du compilateur classique.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schéma des paramètres du fournisseur de langage et du compilateur](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
