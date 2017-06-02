---
title: "URI &#224; en-t&#234;te pack dans WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestion d'applications (WPF)"
  - "charger des ressources incorporées"
  - "charger des fichiers autres que des fichiers de ressources"
  - "schéma URI à en-tête pack"
  - "Uniform Resource Identifiers (URI)"
  - "URI (Uniform Resource Identifiers)"
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# URI &#224; en-t&#234;te pack dans WPF
Dans [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], des [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] sont utilisés pour identifier et charger des fichiers de différentes manières, notamment :  
  
-   en spécifiant l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] à afficher au premier démarrage d'une application ;  
  
-   en chargeant des images ;  
  
-   en accédant à des pages ;  
  
-   en chargeant des fichiers de données non exécutables.  
  
 En outre, les [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] peuvent être utilisés pour identifier et charger des fichiers à partir de divers emplacements, notamment :  
  
-   l'assembly actuel ;  
  
-   un assembly référencé ;  
  
-   un emplacement relatif à un assembly ;  
  
-   le site d'origine de l'application.  
  
 Pour fournir un mécanisme cohérent d'identification et de chargement de ces types de fichiers à partir de ces emplacements, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tire parti de l'extensibilité du *modèle URI à en\-tête pack*.  Cette rubrique fournit une vue d'ensemble du modèle, explique comment construire des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack pour divers scénarios, décrit la résolution des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] et [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] absolus et relatifs et enfin, démontre comment utiliser les [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack à partir des balises et du code.  
  
   
  
<a name="The_Pack_URI_Scheme"></a>   
## Modèle URI à en\-tête pack  
 Le modèle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack est utilisé par la spécification [OPC \(Open Packaging Conventions\)](http://go.microsoft.com/fwlink/?LinkID=71255), qui décrit un modèle d'organisation et d'identification de contenu.  Les principaux éléments de ce modèle sont des packages et des parties, un *package* étant le conteneur logique d'une ou de plusieurs *parties* logiques.  La figure suivante illustre ce concept.  
  
 ![Diagramme Package et pièces](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.png "WPFPackURISchemeFigure1")  
  
 Pour identifier des parties, la spécification OPC tire parti de l'extensibilité de la RFC 2396 \(Uniform Resource Identifiers \(URI\): Generic Syntax\) pour définir le modèle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack.  
  
 Le modèle spécifié par un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] est défini par son préfixe ; http, ftp et file en sont des exemples connus.  Le modèle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack utilise l'en\-tête "pack" comme modèle et contient deux composants : autorité et chemin d'accès.  Un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack se présente au format suivant :  
  
 pack:\/\/*autorité*\/*chemin d'accès*  
  
 L'*autorité* désigne le type de package contenant une partie alors que le *chemin d'accès* indique l'emplacement d'une partie dans un package.  
  
 Ce concept est illustré ci\-dessous :  
  
 ![Relation entre package, autorité et chemin d'accès](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.png "WPFPackURISchemeFigure2")  
  
 Les packages et les parties sont analogues aux applications et aux fichiers, une application \(package\) pouvant contenir un ou plusieurs fichiers \(parties\), notamment :  
  
-   les fichiers de ressources compilés dans l'assembly local ;  
  
-   les fichiers de ressources compilés dans un assembly référencé ;  
  
-   les fichiers de ressources compilés dans un assembly de référence ;  
  
-   les fichiers de contenu ;  
  
-   les fichiers du site d'origine.  
  
 Pour accéder à ces types de fichiers, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend en charge deux autorités : application:\/\/\/ et siteoforigin:\/\/\/.  L'autorité application:\/\/\/ identifie les fichiers de données d'application connus au moment de la compilation, notamment les fichiers de ressources et de contenu.  L'autorité siteoforigin:\/\/\/ identifie les fichiers du site d'origine.  Le domaine de compétence de chaque autorité est indiqué dans la figure suivante.  
  
 ![Diagramme URI à en&#45;tête pack](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  Le composant d'autorité d'un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack est un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] incorporé qui pointe vers un package et doit être conforme à la norme RFC 2396.  En outre, le caractère « \/ » doit être remplacé par le caractère « , » et les caractères réservés tels que « % » et « ?» doivent être placés dans une séquence d'échappement.  Pour plus d'informations, consultez l'OPC.  
  
 Les sections suivantes expliquent comment construire l'[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack à l'aide de ces deux autorités conjointement avec les chemins d'accès appropriés pour identifier les fichiers de ressources, de contenu et du site d'origine.  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## URI à en\-tête pack de fichiers de ressources  
 Les fichiers de ressources sont configurés en tant qu'éléments [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource`et sont compilés dans des assemblys.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prend en charge la construction des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack permettant d'identifier les fichiers de ressources qui sont compilés dans l'assembly local ou dans un assembly référencé à partir de l'assembly local.  
  
<a name="Local_Assembly_Resource_File"></a>   
### Fichier de ressources dans l'assembly local  
 L'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de ressources compilé dans l'assembly local utilise l'autorité et le chemin d'accès suivants :  
  
-   **Autorité** : application:\/\/\/.  
  
-   **Chemin d'accès** : nom du fichier de ressources, y compris son chemin d'accès, relatif à la racine du dossier du projet de l'assembly local.  
  
 L'exemple suivant illustre l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans la racine du dossier du projet de l'assembly local.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 L'exemple suivant illustre l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans un sous\-dossier du dossier du projet de l'assembly local.  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### Fichier de ressources dans un assembly référencé  
 L'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de ressources compilé dans un assembly référencé utilise l'autorité et le chemin d'accès suivants :  
  
-   **Autorité** : application:\/\/\/.  
  
-   **Chemin d'accès** : nom d'un fichier de ressources compilé dans un assembly référencé.  Le chemin d'accès doit respecter le format suivant :  
  
     *NomCourtAssembly*\[*;Version*\]\[*;CléPublique*\];component\/*Chemin d'accès*  
  
    -   **NomCourtAssembly** : nom court de l'assembly référencé.  
  
    -   **;Version** \[facultatif\] : version de l'assembly référencé qui contient le fichier de ressources.  Ce paramètre est utilisé si au moins deux assemblys référencés portant le même nom court sont chargés.  
  
    -   **;CléPublique** \[facultatif\] : clé publique utilisée pour signer l'assembly référencé.  Ce paramètre est utilisé si au moins deux assemblys référencés portant le même nom court sont chargés.  
  
    -   **;component** : indique que l'assembly désigné est référencé à partir de l'assembly local.  
  
    -   **\/Chemin d'accès** : nom du fichier de ressources, y compris son chemin d'accès, relatif à la racine du dossier du projet de l'assembly référencé.  
  
 L'exemple suivant illustre l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans la racine du dossier du projet de l'assembly référencé.  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 L'exemple suivant illustre l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans un sous\-dossier du dossier du projet de l'assembly référence.  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 L'exemple suivant illustre l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de ressources [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui se trouve dans le dossier racine du dossier du projet d'un assembly référencé spécifique à la version.  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 Notez que la syntaxe de l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack des fichiers de ressources d'un assembly référencé ne peut être utilisée qu'avec l'autorité application:\/\/\/.  Par exemple, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne prend pas en charge ce qui suit :  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## URI à en\-tête pack de fichiers de contenu  
 L'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de contenu utilise l'autorité et le chemin d'accès suivants :  
  
-   **Autorité** : application:\/\/\/.  
  
-   **Chemin d'accès** : nom du fichier de contenu, y compris son chemin d'accès relatif à l'emplacement dans le système de fichiers de l'assembly exécutable principal de l'application.  
  
 L'exemple suivant indique l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], qui se trouve dans le même dossier que l'assembly exécutable.  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 L'exemple suivant indique l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier de contenu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], qui se trouve dans un sous\-dossier relatif à l'assembly exécutable de l'application.  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  Il n'est pas possible d'accéder aux fichiers de contenu [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)].  Le modèle [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] prend uniquement en charge la navigation vers les fichiers [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] qui se trouvent au site d'origine.  
  
<a name="The_siteoforigin_____Authority"></a>   
## URI à en\-tête pack du site d'origine  
 L'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier du site d'origine utilise l'autorité et le chemin d'accès suivants :  
  
-   **Autorité** : siteoforigin:\/\/\/.  
  
-   **Chemin d'accès** : nom du fichier du site d'origine, y compris son chemin d'accès relatif à l'emplacement à partir duquel l'assembly exécutable a été lancé.  
  
 L'exemple suivant indique l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier du site d'origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], qui est stocké à l'emplacement à partir duquel l'assembly exécutable est lancé.  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 L'exemple suivant indique l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack d'un fichier du site d'origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], qui est stocké dans un sous\-dossier relatif à l'emplacement à partir duquel l'assembly exécutable de l'application est lancé.  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## Fichiers d'échange  
 Les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] configurés comme éléments `Page` [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] sont compilés dans des assemblys de la même façon que les fichiers de ressources.  Par conséquent, les éléments `Page` [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] peuvent être identifiés à l'aide des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack des fichiers de ressources.  
  
 Les types de fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] généralement configurés comme des éléments `Page` [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] ont l'un des éléments suivants comme racine :  
  
-   <xref:System.Windows.Window?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=fullName>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=fullName>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=fullName>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=fullName>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## Différences entre les URI à en\-tête pack absoluset relatifs  
 Un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack complet comprend le modèle, l'autorité et le chemin d'accès, et il est considéré comme un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack absolu.  Par souci de simplification pour les développeurs, les éléments [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vous permettent en général de définir des attributs appropriés avec un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack relatif, qui ne comprend que le chemin d'accès.  
  
 Prenez par exemple l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack absolu suivant d'un fichier de ressources dans l'assembly local.  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 L'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack qui fait référence à ce fichier de ressources serait le suivant.  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  Étant donné que les fichiers du site d'origine ne sont pas associés aux assemblys, ils ne peuvent être désignés que par des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack absolus.  
  
 Par défaut, un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack est considéré comme relatif à l'emplacement de la balise ou du code qui contient la référence.  Toutefois, si une barre oblique inverse de début est utilisée, la référence de l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack relatif est alors considérée comme étant relative à la racine de l'application.  Prenez par exemple la structure de projet suivante :  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Si Page1.xaml contient un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à *Racine*\\Sous\_dossier\\Page2.xaml, la référence peut utiliser l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack relatif suivant.  
  
 `Page2.xaml`  
  
 Si Page1.xaml contient un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à *Racine*\\Page2.xaml, la référence peut alors utiliser l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack relatif suivant.  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## Résolution des URI à en\-tête pack  
 Le format des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack permet d'attribuer la même apparence aux [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack de différents types de fichiers.  Prenez par exemple l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack absolu suivant.  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 Cet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack absolu pourrait faire référence à un fichier de ressources dans l'assembly local ou à un fichier de contenu.  Il en va de même pour l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] relatif suivant.  
  
 `/ResourceOrContentFile.xaml`  
  
 Pour déterminer le type de fichier auquel fait référence un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] résout les [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] des fichiers de ressources dans les assemblys locaux et des fichiers de contenu à l'aide de l'heuristique suivante :  
  
1.  Recherchez dans les métadonnées de l'assembly un attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> correspondant à l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack.  
  
2.  Si l'attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est détecté, le chemin d'accès de l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack fait référence à un fichier de contenu.  
  
3.  Si l'attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est introuvable, recherchez les fichiers de ressources définis qui sont compilés dans l'assembly local.  
  
4.  Si un fichier de ressources correspondant au chemin d'accès de l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack est détecté, le chemin d'accès de l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack fait référence à un fichier de ressources.  
  
5.  Si la ressource est introuvable, l'<xref:System.Uri> créé en interne n'est pas valide.  
  
 La résolution de l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ne sollicite pas l'[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui fait référence aux éléments suivants :  
  
-   Fichiers de contenu dans les assemblys référencés : ces types de fichiers ne sont pas pris en charge par [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
-   Fichiers incorporés dans les assemblys référencés : les [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui les identifient sont uniques car ils comprennent à la fois le nom de l'assembly référencé et le suffixe `;component`.  
  
-   Fichiers du site d'origine : les [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] qui les identifient sont uniques car ce sont les seuls fichiers qui peuvent être identifiés par des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack contenant l'autorité siteoforigin:\/\/\/.  
  
 Une simplification permise par la résolution de l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack réside dans le fait que le code peut être quelque peu indépendant des emplacements des fichiers de ressource et de contenu.  Par exemple, si l'assembly local contient un fichier de ressources qui est reconfiguré en un fichier de contenu, l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack de la ressource reste identique, de même que le code utilisant cet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
<a name="Programming_with_Pack_URIs"></a>   
## Programmation avec des URI à en\-tête pack  
 De nombreuses classes [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] implémentent des propriétés qui peuvent être définies avec des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack, notamment :  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=fullName>  
  
 Ces propriétés peuvent être définies à partir des balises et du code à la fois.  Cette section démontre les constructions de base des deux, puis fournit des exemples de scénarios courants.  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### Utilisation des URI à en\-tête pack dans les balises  
 Un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack est spécifié dans les balises en définissant l'élément d'un attribut avec l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack.  Par exemple :  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 Le tableau 1 illustre les différents [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack absolus que vous pouvez spécifier dans des balises.  
  
 Tableau 1 : URI à en\-tête pack absolus dans les balises  
  
|Fichier|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack absolu|  
|-------------|-----------------------------------------------------------------------------------------|  
|Fichier de ressources \- assembly local|`"pack://application:,,,/ResourceFile.xaml"`|  
|Fichier de ressources dans un sous\-dossier \- assembly local|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|Fichier de ressources \- assembly référencé|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Fichier de ressources dans un sous\-dossier de l'assembly référencé|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Fichier de ressources dans l'assembly référencé spécifique à la version|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|Fichier de contenu|`"pack://application:,,,/ContentFile.xaml"`|  
|Fichier de contenu dans un sous\-dossier|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|Fichier du site d'origine.|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|Fichier du site d'origine dans un sous\-dossier|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 Le tableau 2 illustre les différents [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack relatifs que vous pouvez spécifier dans des balises.  
  
 Tableau 2 : URI à en\-tête pack relatifs dans les balises  
  
|Fichier|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack relatif|  
|-------------|------------------------------------------------------------------------------------------|  
|Fichier de ressources dans l'assembly local|`"/ResourceFile.xaml"`|  
|Fichier de ressources dans un sous\-dossier de l'assembly local|`"/Subfolder/ResourceFile.xaml"`|  
|Fichier de ressources dans un assembly référencé|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|Fichier de ressources dans un sous\-dossier de l'assembly référencé|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|Fichier de contenu|`"/ContentFile.xaml"`|  
|Fichier de contenu dans un sous\-dossier|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### Utilisation des URI à en\-tête pack dans le code  
 Vous spécifiez un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack dans le code en instanciant la classe <xref:System.Uri> et en transmettant l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack comme un paramètre au constructeur.  Cela est illustré par l'exemple suivant.  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 Par défaut, la classe <xref:System.Uri> considère les [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack comme étant absolus.  Par conséquent, une exception est déclenchée lorsqu'une instance de la classe <xref:System.Uri> est créée avec un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack relatif.  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 Heureusement, la surcharge <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> du constructeur de classe <xref:System.Uri> accepte un paramètre de type <xref:System.UriKind> pour vous permettre de spécifier si un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack est absolu ou relatif.  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml", UriKind.Relative);  
```  
  
 Vous devez spécifier uniquement <xref:System.UriKind> ou <xref:System.UriKind> lorsque vous êtes certain que l'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack est l'un ou l'autre.  Si vous ne connaissez pas le type d'[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack utilisé, comme c'est le cas lorsqu'un utilisateur entre un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack au moment de l'exécution, utilisez plutôt <xref:System.UriKind>.  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 Le tableau 3 illustre les différents [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack relatifs que vous pouvez spécifier dans le code en utilisant <xref:System.Uri?displayProperty=fullName>.  
  
 Tableau 3 : URI à en\-tête pack absolus dans le code  
  
|Fichier|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack absolu|  
|-------------|-----------------------------------------------------------------------------------------|  
|Fichier de ressources \- assembly local|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|Fichier de ressources dans un sous\-dossier \- assembly local|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Fichier de ressources \- assembly référencé|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Fichier de ressources dans un sous\-dossier de l'assembly référencé|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|Fichier de ressources dans l'assembly référencé spécifique à la version|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|Fichier de contenu|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|Fichier de contenu dans un sous\-dossier|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|Fichier du site d'origine.|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|Fichier du site d'origine dans un sous\-dossier|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 Le tableau 4 illustre les différents [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack relatifs que vous pouvez spécifier dans le code en utilisant <xref:System.Uri?displayProperty=fullName>.  
  
 Tableau 4 : URI à en\-tête pack relatifs dans le code  
  
|Fichier|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack relatif|  
|-------------|------------------------------------------------------------------------------------------|  
|Fichier de ressources \- assembly local|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|Fichier de ressources dans un sous\-dossier \- assembly local|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Fichier de ressources \- assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|Fichier de ressources dans un sous\-dossier \- assembly référencé|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|Fichier de contenu|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|Fichier de contenu dans un sous\-dossier|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### Scénarios courants utilisant des URI à en\-tête pack  
 Les sections précédentes ont expliqué comment construire des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack pour identifier des fichiers de ressources, de contenu et du site d'origine.  Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], ces constructions sont utilisées de diverses manières et les sections suivantes en décrivent plusieurs usages courants.  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### Spécification de l'interface utilisateur à afficher au démarrage d'une application  
 <xref:System.Windows.Application.StartupUri%2A> spécifie la première [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à afficher lorsqu'une application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] est lancée.  Pour les applications autonomes, l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] peut être une fenêtre, comme illustré dans l'exemple suivant.  
  
 [!code-xml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 Les applications autonomes et les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] peuvent également spécifier une page comme interface utilisateur initiale, comme illustré dans l'exemple suivant.  
  
 [!code-xml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 Si l'application est une application autonome et une page est spécifiée avec <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ouvre une <xref:System.Windows.Navigation.NavigationWindow> pour héberger la page.  Pour les [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], la page est affichée dans le navigateur hôte.  
  
<a name="Navigating_to_a_Page"></a>   
#### Navigation jusqu'à une page  
 L'exemple suivant indique comment naviguer jusqu'à une page.  
  
 [!code-xml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 Pour plus d'informations sur les différentes méthodes de navigation dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consultez [Vue d'ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Specifying_a_Window_Icon"></a>   
#### Spécification d'une icône de fenêtre  
 L'exemple suivant indique comment utiliser un URI pour spécifier l'icône d'une fenêtre.  
  
 [!code-xml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 Pour plus d'informations, consultez <xref:System.Windows.Window.Icon%2A>.  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### Chargement de fichiers image, audio et vidéo  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet aux applications d'utiliser une large gamme de types de médias, qui peuvent tous être identifiés et chargés avec les [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack, comme illustré dans les exemples suivants.  
  
 [!code-xml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 Pour plus d'informations sur l'utilisation de contenus multimédias, consultez [Graphiques et multimédia](../../../../docs/framework/wpf/graphics-multimedia/index.md).  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### Chargement d'un dictionnaire de ressources à partir du site d'origine  
 Les dictionnaires de ressources \(<xref:System.Windows.ResourceDictionary>\) peuvent être utilisés pour prendre en charge des thèmes d'application.  Une façon de créer et de gérer des thèmes consiste en la création de plusieurs thèmes, comme des dictionnaires de ressources, qui se trouvent au site d'origine d'une application.  Cela permet d'ajouter et de mettre à jour des thèmes sans avoir à recompiler et redéployer une application.  Ces dictionnaires de ressources peuvent être identifiés et chargés à l'aide d'[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack, qui sont illustrés dans l'exemple suivant.  
  
 [!code-xml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 Pour une vue d'ensemble des thèmes dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## Voir aussi  
 [Fichiers de ressources, de contenu et de données d'une application WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)