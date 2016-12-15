---
title: "/appconfig (C# Compiler Options) | Microsoft Docs"
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
  - "/appconfig"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/appconfig compiler option [C#]"
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /appconfig (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'option de compilateur **\/appconfig** permet à une application C\# d'indiquer l'emplacement du fichier de configuration d'application \(app.config\) d'un assembly au Common Language Runtime \(CLR\) au moment de la liaison de l'assembly.  
  
## Syntaxe  
  
```  
/appconfig:file  
```  
  
## Arguments  
 `file`  
 Obligatoire.  Fichier de configuration de l'application qui contient des paramètres de liaison d'assembly.  
  
## Notes  
 **\/appconfig** est notamment utilisé dans des scénarios avancés dans lesquels un assembly doit simultanément référencer à la fois la version du .NET Framework et la version du .NET Framework pour Silverlight d'un assembly de référence particulier.  Par exemple, un concepteur XAML écrit dans Windows Presentation Foundation \(WPF\) devra peut\-être référencer à la fois le bureau WPF pour l'interface utilisateur du concepteur et le sous\-ensemble de WPF qui est fourni avec Silverlight.  Le même concepteur d'assembly doit accéder aux deux assemblys.  Par défaut, les références séparées provoquent une erreur du compilateur, parce que la liaison d'assembly considère les deux assemblys comme équivalents.  
  
 L'option de compilateur **\/appconfig** vous permet de spécifier l'emplacement d'un fichier app.config qui désactive le comportement par défaut à l'aide d'une balise `<supportPortability>`, comme indiqué dans l'exemple suivant.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 Le compilateur passe l'emplacement du fichier à la logique de liaison d'assembly du CLR.  
  
> [!NOTE]
>  Si vous utilisez Microsoft Build Engine \(MSBuild\) pour générer votre application, vous pouvez définir l'option du compilateur **\/appconfig** en ajoutant une balise de propriété au fichier .csproj.  Pour utiliser le fichier app.config qui est déjà défini dans le projet, ajoutez la balise `<UseAppConfigForCompiler>` de propriétés au fichier .csproj et affectez \-lui la valeur `true`.  Pour spécifier un autre fichier app.config, ajoutez la balise `<AppConfigForCompiler>` de propriété et définissez sa valeur à l'emplacement du fichier.  
  
## Exemple  
 L'exemple suivant affiche un fichier app.config qui permet à une application d'avoir des références à la fois à l'implémentation de .NET Framework et au .NET Framework pour l'implémentation Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations.  L'option de compilateur **\/appconfig** spécifie l'emplacement de ce fichier app.config.  
  
```  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [.NET Framework Assembly Unification Overview](http://msdn.microsoft.com/fr-fr/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)   
 [\<supportPortability\>, élément](../Topic/%3CsupportPortability%3E%20Element.md)   
 [C\# Compiler Options Listed Alphabetically](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)