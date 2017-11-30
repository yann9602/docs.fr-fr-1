---
title: "Fichiers de ressources, de contenu et de données d'une application WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19fd82daabd5ed12776b2deee6bc850529a6ef23
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="wpf-application-resource-content-and-data-files"></a>Fichiers de ressources, de contenu et de données d'une application WPF
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]applications dépendent souvent de fichiers qui contiennent des données non exécutables, tels que [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, vidéo et audio. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] assure une prise en charge spéciale pour la configuration, l’identification et l’utilisation de ces types de fichier de données, appelés fichiers de données d’application. Cette prise en charge repose sur un ensemble spécifique de types de fichier de données d’application, notamment :  
  
-   **Fichiers de ressources**: fichiers de données qui sont compilés dans un fichier exécutable ou une bibliothèque [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
-   **Fichiers de contenu**: fichiers de données autonomes possédant une association explicite avec un fichier exécutable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
-   **Fichiers d’origine du site de**: fichiers de données autonomes qui disposent d’aucune association avec un fichier exécutable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
 Il existe une distinction importante entre ces trois types de fichier : les fichiers de ressources et les fichiers de contenu sont connus au moment de la génération. En effet, un assembly les connaît explicitement. Pour les fichiers du site d’origine, toutefois, un assembly ne peut avoir aucune connaissance du tout, ou une connaissance implicite via un pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] référence ; le cas de ce dernier, il n’existe aucune garantie que le site référencé du fichier d’origine existe réellement.  
  
 Pour référencer des fichiers de données d’application, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] utilise le Pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] schéma, ce qui est décrit en détail dans [URI à en-tête Pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 Cette rubrique décrit comment configurer et utiliser des fichiers de données d’application.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Fichiers de ressources  
 Si un fichier de données d’application doit toujours être disponible pour une application, le seul moyen de garantir cette disponibilité est de le compiler en un assembly exécutable principal d’une application ou en l’un de ses assemblys référencés. Ce type de fichier de données d’application est connu comme un *fichier de ressources*.  
  
 Vous devez utiliser des fichiers de ressources dans les situations suivantes :  
  
-   Vous n’avez pas besoin de mettre à jour le contenu du fichier de ressources une fois qu’il a été compilé en un assembly.  
  
-   Vous souhaitez simplifier la complexité de distribution d’une application en réduisant le nombre des dépendances de fichiers.  
  
-   Votre fichier de données d’application doit être localisable (consultez [vue d’ensemble de la localisation et de globalisation de WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Les fichiers de ressources décrites dans cette section sont différentes de celles décrites par les fichiers de ressources dans [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) et différent de celui de ressources incorporés ou liés décrits dans [ressources de gestion de l’Application (.NET) ](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Configuration des fichiers de ressources  
 Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], un fichier de ressources est un fichier qui est inclus dans un [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] de projet comme un `Resource` élément.  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vous créez un fichier de ressources en ajoutant un fichier à un projet et en définissant son `Build Action` à `Resource`.  
  
 Lorsque le projet est généré, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] compile la ressource dans l’assembly.  
  
### <a name="using-resource-files"></a>Utilisation des fichiers de ressources  
 Pour charger un fichier de ressources, vous pouvez appeler la <xref:System.Windows.Application.GetResourceStream%2A> méthode de la <xref:System.Windows.Application> classe, en passant un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui identifie le fichier de ressources de votre choix. <xref:System.Windows.Application.GetResourceStream%2A>Retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet, qui expose le fichier de ressources comme une <xref:System.IO.Stream> et décrit son type de contenu.  
  
 Par exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetResourceStream%2A> pour charger un <xref:System.Windows.Controls.Page> ressources de fichiers et définissez-le en tant que le contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`) :  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Lors de l’appel <xref:System.Windows.Application.GetResourceStream%2A> vous donne accès à la <xref:System.IO.Stream>, vous devez exécuter le travail supplémentaire de conversion vers le type de la propriété que vous définirez avec. Au lieu de cela, vous pouvez laisser [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prenez soin d’ouvrir et de convertir la <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide de code.  
  
 L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide de code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Fichiers de code d’application en tant que fichiers de ressources  
 Une spéciale définie de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fichiers de code d’application peuvent être référencés à l’aide du pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], notamment windows, les pages, les documents de flux et les dictionnaires de ressources. Par exemple, vous pouvez définir le <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> propriété avec un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui fait référence à la fenêtre ou la page que vous souhaitez charger au démarrage d’une application.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Vous pouvez le faire lorsque un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est inclus dans un [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] de projet comme un `Page` élément.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous ajoutez un nouveau <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, ou <xref:System.Windows.ResourceDictionary> à un projet, le `Build Action` du balisage fichier par défaut est `Page`.  
  
 Lorsqu’un projet avec `Page` éléments est compilé, les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] éléments sont convertis au format binaire et compilés dans l’assembly associé. Ainsi, ces fichiers peuvent être utilisés de la même façon que des fichiers de ressources classiques.  
  
> [!NOTE]
>  Si un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier est configuré comme un `Resource` d’élément et n’a pas d’un fichier code-behind, le texte brut [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est compilé dans un assembly plutôt qu’une version binaire de brute [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Fichiers de contenu  
 A *fichier de contenu* est distribué comme un fichier libre en même temps que d’un assembly exécutable. Bien qu’ils ne soient pas compilés en un assembly, les assemblys sont compilés à l’aide de métadonnées qui établissent une association avec chaque fichier de contenu.  
  
 Vous devez utiliser des fichiers de contenu quand votre application nécessite un ensemble spécifique de fichiers de données d’application, que vous souhaitez pouvoir mettre à jour sans recompiler l’assembly qui les consomme.  
  
### <a name="configuring-content-files"></a>Configuration des fichiers de contenu  
 Pour ajouter un fichier de contenu à un projet, un fichier de données d’application doit être inclus en tant qu’un `Content` élément. En outre, comme un fichier de contenu n’est pas compilé directement dans l’assembly, vous devez définir le [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` élément de métadonnées pour spécifier que le fichier de contenu est copié vers un emplacement qui est relatif à l’assembly généré. Si vous souhaitez que la ressource à copier dans le dossier de sortie de génération chaque fois qu’un projet est généré, vous définissez la `CopyToOutputDirectory` élément de métadonnées avec le `Always` valeur. Sinon, vous pouvez vous assurer qu’uniquement la version la plus récente de la ressource est copiée dans le dossier de sortie de génération à l’aide de la `PreserveNewest` valeur.  
  
 L’exemple ci-dessous illustre un fichier configuré en tant que fichier de contenu copié dans le dossier de sortie de build uniquement quand une nouvelle version de la ressource est ajoutée au projet.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous créez un fichier de contenu en ajoutant un fichier à un projet et en définissant son `Build Action` à `Content`et définir son `Copy to Output Directory` à `Copy always` (identique `Always`) et `Copy if newer` (identique `PreserveNewest`).  
  
 Lorsque le projet est généré, un <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribut est compilé dans les métadonnées de l’assembly pour chaque fichier de contenu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 La valeur de la <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implique le chemin d’accès au fichier de contenu par rapport à sa position dans le projet. Par exemple, si un fichier de contenu était situé dans un sous-dossier de projet, les informations de chemin d’accès supplémentaire sont intégrées à la <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valeur.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 Le <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valeur est également la valeur du chemin d’accès au fichier de contenu dans le dossier de sortie de génération.  
  
### <a name="using-content-files"></a>Utilisation des fichiers de contenu  
 Pour charger un fichier de contenu, vous pouvez appeler la <xref:System.Windows.Application.GetContentStream%2A> méthode de la <xref:System.Windows.Application> classe, en passant un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui identifie le fichier de contenu souhaité. <xref:System.Windows.Application.GetContentStream%2A>Retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet, qui expose le fichier de contenu comme un <xref:System.IO.Stream> et décrit son type de contenu.  
  
 Par exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetContentStream%2A> pour charger un <xref:System.Windows.Controls.Page> fichier de contenu et définissez-le en tant que le contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Lors de l’appel <xref:System.Windows.Application.GetContentStream%2A> vous donne accès à la <xref:System.IO.Stream>, vous devez exécuter le travail supplémentaire de conversion vers le type de la propriété que vous définirez avec. Au lieu de cela, vous pouvez laisser [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prenez soin d’ouvrir et de convertir la <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide de code.  
  
 L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide de code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Fichiers du site d’origine  
 Fichiers de ressources ont une relation explicite avec les assemblys qu’ils sont distribués, comme défini par le <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Toutefois, vous pouvez être amené à établir une relation implicite ou inexistante entre un assembly et un fichier de données d’application, notamment dans les situations suivantes :  
  
-   Un fichier n’existe pas au moment de la compilation.  
  
-   Vous ignorez de quels fichiers votre assembly a besoin jusqu’au moment de l’exécution.  
  
-   Vous souhaitez pouvoir mettre à jour des fichiers sans recompiler l’assembly auquel ils sont associés.  
  
-   Votre application utilise des fichiers de données volumineux, par exemple des fichiers audio et vidéo, et vous souhaitez que les utilisateurs aient le choix de les télécharger ou non.  
  
 Il est possible de charger ces types de fichiers à l’aide de traditionnels [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schémas, tels que les modèles file:/// et http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Toutefois, pour les schémas file:/// et http:// votre application doit bénéficier d’une confiance totale. Si votre application est un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] qui a été lancé à partir d’Internet ou intranet et seulement le jeu d’autorisations qui sont autorisées pour les applications lancées à partir de ces emplacements, fichiers libres ne peuvent être chargés à partir du site de l’application d’origine (des demandes emplacement de lancement). Ces fichiers sont appelés *site d’origine* fichiers.  
  
 Les fichiers du site d’origine sont la seule option pour les applications partiellement fiables. Toutefois, ils ne se limitent pas à ces applications. Les applications entièrement fiables peuvent tout de même avoir besoin de charger des fichiers de données d’application dont ils n’ont pas connaissance au moment de la génération. Bien que les applications entièrement fiables puissent utiliser file:///, les fichiers de données d’application sont probablement installés dans le même dossier ou sous-dossier que l’assembly d’application. Dans ce cas, l’utilisation du référencement du site d’origine est plus facile que l’utilisation de file:///, car avec file:/// vous devez résoudre le chemin complet du fichier.  
  
> [!NOTE]
>  Site d’origine, les fichiers ne sont pas mis en cache avec un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] sur un ordinateur client, tandis que les fichiers de contenu. Ils sont donc téléchargés à la demande. Si un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] contient des fichiers multimédias volumineux, les configurer comme site de fichiers d’origine signifie que le lancement de l’application initiale est beaucoup plus rapide, et les fichiers sont téléchargés uniquement à la demande.  
  
### <a name="configuring-site-of-origin-files"></a>Configuration des fichiers du site d’origine  
 Si vos fichiers du site d’origine est inexistants ou inconnus au moment de la compilation, vous devez utiliser le déploiement classique mécanismes pour garantir que les fichiers requis sont disponibles au moment de l’exécution, notamment en utilisant soit le `XCopy` programme de ligne de commande ou la [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Si vous connaissez au moment de la compilation, les fichiers que vous aimeriez voir situés sur le site d’origine, mais toujours vouloir éviter une dépendance explicite, vous pouvez ajouter ces fichiers à un [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] de projet comme `None` élément. Comme avec les fichiers de contenu, vous devez définir le [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` attribut pour spécifier que le fichier du site d’origine est copié vers un emplacement relatif à l’assembly généré, en spécifiant soit le `Always` valeur ou la `PreserveNewest` valeur.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous créez un fichier du site d’origine en ajoutant un fichier à un projet et en définissant son `Build Action` à `None`.  
  
 Lorsque le projet est généré, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] copie les fichiers spécifiés dans le dossier de sortie de génération.  
  
### <a name="using-site-of-origin-files"></a>Utilisation des fichiers du site d’origine  
 Pour charger un fichier du site d’origine, vous pouvez appeler la <xref:System.Windows.Application.GetRemoteStream%2A> méthode de la <xref:System.Windows.Application> classe, en passant un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui identifie le site souhaité du fichier d’origine. <xref:System.Windows.Application.GetRemoteStream%2A>Retourne un <xref:System.Windows.Resources.StreamResourceInfo> objet, qui expose le site du fichier d’origine comme un <xref:System.IO.Stream> et décrit son type de contenu.  
  
 Par exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetRemoteStream%2A> pour charger un <xref:System.Windows.Controls.Page> site d’origine du fichier et définissez-le en tant que le contenu d’un <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Lors de l’appel <xref:System.Windows.Application.GetRemoteStream%2A> vous donne accès à la <xref:System.IO.Stream>, vous devez exécuter le travail supplémentaire de conversion vers le type de la propriété que vous définirez avec. Au lieu de cela, vous pouvez laisser [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prenez soin d’ouvrir et de convertir la <xref:System.IO.Stream> en chargeant un fichier de ressources directement dans la propriété d’un type à l’aide de code.  
  
 L’exemple suivant montre comment charger un <xref:System.Windows.Controls.Page> directement dans un <xref:System.Windows.Controls.Frame> (`pageFrame`) à l’aide de code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 L’exemple suivant est l’équivalent sous forme de balisage de l’exemple précédent.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Regénération après changement du type de build  
 Après avoir changé le type de build d’un fichier de données d’application, vous devez regénérer l’application entière pour vérifier que ces changements sont bien appliqués. Si vous générez uniquement l’application, les changements ne sont pas appliqués.  
  
## <a name="see-also"></a>Voir aussi  
 [URI à en-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
