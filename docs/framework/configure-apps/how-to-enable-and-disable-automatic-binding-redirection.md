---
title: "Comment&#160;: activer et d&#233;sactiver la redirection de liaison automatique | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "assemblys (.NET Framework), redirection de liaison"
  - "exécution côte à côte, redirection de liaison d'assembly"
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# Comment&#160;: activer et d&#233;sactiver la redirection de liaison automatique
Depuis [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], lorsque vous compilez des applications qui ciblent [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], des redirections de liaison peuvent être ajoutées automatiquement au fichier de configuration d'application pour remplacer l'unification d'assemblys.  Les redirections de liaison sont ajoutées si votre application ou ses composants font référence à plusieurs versions du même assembly, même si vous spécifiez manuellement des redirections de liaison dans le fichier de configuration de votre application.  La fonctionnalité de redirection de liaison automatique affecte les applications de bureau et les applications web traditionnelles qui ciblent [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], bien que le comportement soit légèrement différent pour une application web.  Vous pouvez activer une redirection de liaison automatique si vos applications existantes ciblent des versions antérieures du .NET Framework, ou vous pouvez désactiver cette fonctionnalité si vous souhaitez conserver les redirections de liaison créées manuellement.  
  
## Désactivation des redirections de liaison automatiques dans les applications de bureau  
 Les redirections de liaison automatiques sont activées par défaut pour les applications de bureau traditionnelles qui ciblent [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] et versions ultérieures.  Les redirections de liaison sont ajoutées au fichier de configuration de sortie \(app.config\) lorsque l'application est compilée et remplace l'unification d'assemblys qui pourrait se produire, dans le cas contraire.  Le fichier source app.config n'est pas modifié.  Vous pouvez désactiver cette fonctionnalité en modifiant le fichier projet pour l'application.  
  
#### Pour désactiver les redirections de liaison automatiques  
  
1.  Dans Visual Studio, sélectionnez le projet dans l'**Explorateur de solutions**, puis choisissez **Ouvrir le dossier dans l'Explorateur de fichiers** dans le menu contextuel.  
  
2.  Dans l'Explorateur de fichiers, recherchez le fichier projet \(.csproj ou .vbproj\) et ouvrez\-le dans le Bloc\-notes.  
  
3.  Dans le fichier projet, recherchez l'entrée de propriété suivante :  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  Remplacez `true` par `false` :  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## Activation manuelle des redirections de liaison automatiques  
 Vous pouvez activer les redirections de liaison automatiques dans les applications existantes qui ciblent des versions plus anciennes de .NET Framework ou quand vous n'êtes pas automatiquement invité à ajouter une redirection.  Si vous ciblez une version plus récente du framework mais que vous n'êtes pas automatiquement invité à ajouter une redirection, une sortie de génération vous suggérera probablement de remapper les assemblys.  
  
#### Pour ajouter manuellement une propriété de redirection de liaison automatique  
  
1.  Dans Visual Studio, sélectionnez le projet dans l'**Explorateur de solutions**, puis choisissez **Ouvrir le dossier dans l'Explorateur de fichiers** dans le menu contextuel.  
  
2.  Dans l'Explorateur de fichiers, recherchez le fichier projet \(.csproj ou .vbproj\) et ouvrez\-le dans le Bloc\-notes.  
  
3.  Ajoutez l'élément suivant au premier groupe de propriétés de configuration \(sous la balise \<PropertyGroup\>\) :  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     Le code suivant illustre un fichier de projet comportant l'élément.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProjectGuid>{123334}</ProjectGuid>  
        ...  
        <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>  
      </PropertyGroup>  
    ...  
    </Project>  
  
    ```  
  
4.  Compilez votre application.  
  
## Activation des redirections de liaison automatiques dans les applications web  
 Les redirections de liaison automatiques sont implémentées différemment pour les applications web.  Comme le fichier de configuration source \(web.config\) doit être modifié pour les applications web, les redirections de liaison ne sont pas automatiquement ajoutées au fichier de configuration.  Toutefois, Visual Studio vous informe des éventuels conflits de liaison et vous pouvez ajouter des redirections de liaison pour résoudre ces conflits.  Comme vous êtes toujours invité à approuver ou non l'ajout des redirections de liaison, vous n'avez pas besoin de désactiver explicitement cette fonctionnalité pour une application web.  
  
#### Pour ajouter des redirections de liaison vers un fichier web.config  
  
1.  Dans Visual Studio, compilez l'application et vérifiez les avertissements sur la génération.  
  
     ![Avertissement sur la génération des conflits de la référence d'assembly](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR\_AssemblyRefWarning")  
  
2.  En cas de conflit de liaison d'assembly, un avertissement s'affiche.  Double\-cliquez sur l'avertissement.  \(Clavier : sélectionnez l'avertissement et appuyez sur **Entrée**.\)  
  
     Une boîte de dialogue apparaît qui vous permet d'ajouter automatiquement les redirections de liaison nécessaires vers le fichier web.config source.  
  
     ![Boîte de dialogue des autorisations de redirection de liaison](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR\_AddBindingRedirect")  
  
## Voir aussi  
 [\<bindingRedirect\>, élément](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)   
 [Redirection des versions d'assemblys](../../../docs/framework/configure-apps/redirect-assembly-versions.md)