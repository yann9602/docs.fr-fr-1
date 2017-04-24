---
title: "Fichiers de ressources, de contenu et de donn&#233;es d&#39;une application WPF | Microsoft Docs"
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
  - "développement d'applications (WPF), fichiers"
  - "gestion d'applications (WPF)"
  - "fichiers de contenu (WPF)"
  - "ressources incorporées (WPF)"
  - "fichiers (WPF)"
  - "ressources libres (WPF)"
  - "référencer des fichiers d'application (WPF)"
  - "fichiers distants (WPF)"
  - "fichiers de ressources (WPF)"
  - "fichiers du site d'origine (WPF)"
  - "application WPF, fichiers"
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Fichiers de ressources, de contenu et de donn&#233;es d&#39;une application WPF
Les applications [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] dépendent souvent de fichiers qui contiennent des données non exécutables, notamment de fichiers [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], d'images, vidéo et audio.  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] assure une prise en charge spéciale pour la configuration, l'identification, et l'utilisation de ces types de fichiers de données, appelés fichiers de données d'application.  Cette prise en charge repose sur un jeu spécifique de types de fichiers de données d'application, y compris :  
  
-   **Fichiers de ressources** : fichiers de données compilés en un fichier exécutable ou un assembly [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] de bibliothèque.  
  
-   **Fichiers de contenu** : fichiers de données autonomes possédant une association explicite avec un assembly [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exécutable.  
  
-   **Fichiers du site d'origine** : fichiers de données autonomes ne possédant aucune association avec un assembly [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exécutable.  
  
 Une distinction importante à faire entre ces trois types de fichiers est que les fichiers de ressources et les fichiers de contenu sont connus au moment de la génération ; un assembly les connaît explicitement.  Pour des fichiers du site d'origine, en revanche, un assembly peut n'avoir aucune connaissance d'eux, ou une connaissance implicite par le biais d'un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] à en\-tête pack de référence ; dans ce dernier cas, il n'y a aucune garantie que le fichier du site d'origine référencé existe réellement.  
  
 Pour référencer des fichiers de données d'application, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] utilise le modèle [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] à en\-tête pack qui est décrit en détail dans [URI à en\-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)\).  
  
 Cette rubrique décrit comment configurer et utiliser des fichiers de données d'application.  
  
   
  
<a name="Resource_Files"></a>   
## Fichiers de ressources  
 Si un fichier de données d'application doit toujours être disponible pour une application, la seule méthode pour garantir cette disponibilité est de le compiler en un assembly exécutable principal d'application ou l'un de ses assemblys référencés.  Ce type de fichier de données d'application est connu sous le nom de *fichier de ressources*.  
  
 Vous devez utiliser des fichiers de ressources lorsque :  
  
-   Vous n'avez pas besoin de mettre à jour le contenu du fichier de ressources après qu'il a été compilé en un assembly.  
  
-   Vous souhaitez simplifier la complexité de distribution d'application en réduisant le nombre de dépendances de fichier.  
  
-   Votre fichier de données d'application doit être localisable \(consultez [Vue d'ensemble de la globalisation et de la localisation WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)\).  
  
> [!NOTE]
>  Les fichiers de ressources décrits dans cette section sont différents que les fichiers de ressources décrites dans [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) et différents que les ressources incorporées ou associées décrites dans [Gestion des ressources d'une application \(.NET\)](../Topic/Managing%20Application%20Resources%20\(.NET\).md).  
  
### Configuration de fichiers de ressources  
 Dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], un fichier de ressources est un fichier inclus dans un projet [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] sous la forme d'un élément `Resource`.  
  
```  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vous créez un fichier de ressources en ajoutant un fichier à un projet et en définissant son `Build Action` sur `Resource`.  
  
 Lorsque le projet est généré, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] compile la ressource en l'assembly.  
  
### Utilisation de fichiers de ressources  
 Pour charger un fichier de ressources, vous pouvez appeler la méthode <xref:System.Windows.Application.GetResourceStream%2A> de la classe <xref:System.Windows.Application>, en passant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack qui identifie le fichier de ressources souhaité.  <xref:System.Windows.Application.GetResourceStream%2A> retourne un objet <xref:System.Windows.Resources.StreamResourceInfo>, qui expose le fichier de ressources en tant que <xref:System.IO.Stream> et décrit son type de contenu.  
  
 À titre d'exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetResourceStream%2A> pour charger un fichier de ressources <xref:System.Windows.Controls.Page> et le définir comme contenu d'un <xref:System.Windows.Controls.Frame> \(`pageFrame`\) :  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Bien que l'appel de <xref:System.Windows.Application.GetResourceStream%2A> vous donne accès à <xref:System.IO.Stream>, vous devez exécuter le travail supplémentaire de conversion vers le type de la propriété avec lequel vous le définirez.  À la place, vous pouvez laisser à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] le soin d'ouvrir et de convertir <xref:System.IO.Stream> en chargeant directement un fichier de ressources dans la propriété d'un type à l'aide du code.  
  
 L'exemple suivant montre comment charger directement un <xref:System.Windows.Controls.Page> dans un <xref:System.Windows.Controls.Frame> \(`pageFrame`\) à l'aide du code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 L'exemple suivant est l'équivalent sous forme de balise de l'exemple précédent.  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### Fichiers de code d'application comme fichiers de ressources  
 Un jeu spécial de fichiers de code d'application [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] peut être référencé à l'aide des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] à en\-tête pack, lesquels comprennent des fenêtres, des pages, des documents dynamiques et des dictionnaires de ressources.  Par exemple, vous pouvez définir la propriété <xref:System.Windows.Application.StartupUri%2A?displayProperty=fullName> avec un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] à en\-tête pack qui référence la fenêtre ou la page que vous aimeriez charger lorsqu'une application démarre.  
  
 [!code-xml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Vous pouvez le faire lorsqu'un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est inclus dans un projet [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] sous la forme d'un élément `Page`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous ajoutez un nouveau <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument> ou <xref:System.Windows.ResourceDictionary> à un projet, `Build Action` pour le fichier de balisage aura comme valeur par défaut `Page`.  
  
 Lorsqu'un projet avec des éléments `Page` est compilé, les éléments [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont convertis en format binaire et compilés dans l'assembly associé.  Par conséquent, ces fichiers peuvent être utilisés de la même façon que des fichiers de ressources typiques.  
  
> [!NOTE]
>  Si un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est configuré comme un élément `Resource`, et qu'il n'a pas de fichier code\-behind, le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] brut est compilé en un assembly plutôt qu'en une version binaire du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] brut.  
  
<a name="Content_Files"></a>   
## Fichiers de contenu  
 Un *fichier de contenu* est distribué comme un fichier libre en même temps qu'un assembly exécutable.  Bien qu'ils ne soient pas compilés en un assembly, ceux\-ci sont compilés avec les métadonnées qui établissent une association avec chaque fichier de contenu.  
  
 Vous devez utiliser des fichiers de contenu lorsque votre application requiert un jeu spécifique de fichiers de données d'application que vous souhaitez pouvoir mettre à jour sans recompiler l'assembly qui les consomme.  
  
### Configuration de fichiers de contenu  
 Pour ajouter un fichier de contenu à un projet, un fichier de données d'application doit être inclus en tant qu'élément `Content`.  En outre, comme un fichier de contenu n'est pas compilé directement dans l'assembly, vous devez définir l'élément de métadonnées [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]```CopyToOutputDirectory` pour spécifier que le fichier de contenu est copié vers un emplacement qui est relatif à l'assembly créé.  Si vous souhaitez que la ressource soit copiée vers le dossier de sortie de génération chaque fois qu'un projet est généré, vous définissez l'élément de métadonnées `CopyToOutputDirectory` avec la valeur `Always`.  Sinon, vous pouvez vous assurer que seule la version la plus récente de la ressource est copiée vers le dossier de sortie de génération en utilisant la valeur `PreserveNewest`.  
  
 Ce qui suit montre un fichier configuré comme un fichier de contenu qui est copié dans le dossier de sortie de génération uniquement lorsqu'une nouvelle version de la ressource est ajoutée au projet.  
  
```  
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
>  Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous créez un fichier de contenu en ajoutant un fichier à un projet et en définissant son `Build Action` à `Content` et vous affecter à son `Copy to Output Directory` la valeur `Copy always` \(identique à `Always`\) et `Copy if newer` \(identique à `PreserveNewest`\).  
  
 Lorsque le projet est généré, un attribut <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est compilé dans les métadonnées de l'assembly pour chaque fichier de contenu.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 La valeur du <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implique le chemin d'accès au fichier contenu par rapport à sa position dans le projet.  Par exemple, si un fichier de contenu était situé dans un sous\-dossier de projet, les informations supplémentaires du chemin d'accès seraient incorporées dans la valeur <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 La valeur <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> est également celle du chemin d'accès au fichier de contenu dans le dossier de sortie de génération.  
  
### Utilisation de fichiers de contenu  
 Pour charger un fichier de contenu, vous pouvez appeler la méthode <xref:System.Windows.Application.GetContentStream%2A> de la classe <xref:System.Windows.Application>, en passant une [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de pack qui identifie le fichier de contenu souhaité.  <xref:System.Windows.Application.GetContentStream%2A> retourne un objet <xref:System.Windows.Resources.StreamResourceInfo>, qui expose le fichier de contenu en tant que <xref:System.IO.Stream> et décrit son type de contenu.  
  
 À titre d'exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetContentStream%2A> pour charger un fichier de contenu <xref:System.Windows.Controls.Page> et le définir comme contenu d'un <xref:System.Windows.Controls.Frame> \(`pageFrame`\).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Bien que l'appel de <xref:System.Windows.Application.GetContentStream%2A> vous donne accès à <xref:System.IO.Stream>, vous devez exécuter le travail supplémentaire de conversion vers le type de la propriété avec lequel vous le définirez.  À la place, vous pouvez laisser à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] le soin d'ouvrir et de convertir <xref:System.IO.Stream> en chargeant directement un fichier de ressources dans la propriété d'un type à l'aide du code.  
  
 L'exemple suivant montre comment charger directement un <xref:System.Windows.Controls.Page> dans un <xref:System.Windows.Controls.Frame> \(`pageFrame`\) à l'aide du code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 L'exemple suivant est l'équivalent sous forme de balise de l'exemple précédent.  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## Fichiers du site d'origine  
 Les fichiers de ressources ont une relation explicite avec les assemblys avec lesquels ils sont distribués, comme défini par <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.  Toutefois, il peut arriver que vous souhaitiez établir une relation implicite ou inexistante entre un assembly et un fichier de données d'application, y compris lorsque :  
  
-   Un fichier n'existe pas lors de la compilation.  
  
-   Vous ignorez de quels fichiers votre assembly aura besoin jusqu'au moment de l'exécution.  
  
-   Vous souhaitez pouvoir mettre des fichiers à jour sans recompiler l'assembly auquel ils sont associés.  
  
-   Votre application utilise des fichiers de données volumineux, tels que des fichiers audio et vidéo, et vous souhaitez que les utilisateurs ne les téléchargent que s'ils choisissent de le faire.  
  
 Il est possible de charger ces types de fichiers en utilisant des modèles [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] traditionnels, tels que les modèles file:\/\/\/ et http:\/\/.  
  
 [!code-xml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Toutefois, les modèles file:\/\/\/ et http:\/\/ requièrent que votre application bénéficient de la confiance totale.  S'il s'agit d'une [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] lancée à partir d'Internet ou d'un intranet, et qu'elle n'a besoin que du jeu des autorisations prévues pour des applications lancées à partir de ces emplacements, des fichiers libres ne peuvent être chargés qu'à partir du site d'origine de l'application \(emplacement de lancement\).  De tels fichiers sont dénommés fichiers du *site d'origine*.  
  
 Les fichiers du site d'origine sont la seule option pour les applications bénéficiant d'une confiance partielle, bien qu'ils ne se limitent aux applications bénéficiant d'une confiance partielle.  Les applications bénéficiant d'une confiance totale peuvent quand même devoir charger des fichiers de données d'application dont ils n'ont pas connaissance lors de la génération ; bien que des applications bénéficiant d'une confiance totale puissent utiliser file:\/\/\/, il est probable que les fichiers de données d'application seront installés dans le même dossier ou sous\-dossier que l'assembly d'application.  Dans ce cas, l'utilisation du référencement du site d'origine est plus facile que l'utilisation de file:\/\/\/, parce que l'utilisation de ce dernier requiert que vous résolviez le chemin d'accès complet du fichier.  
  
> [!NOTE]
>  Les fichiers du site d'origine ne sont pas mis en mémoire cache avec une [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] sur un ordinateur client, alors que les fichiers de contenu le sont.  Par conséquent, ils sont téléchargés uniquement lorsqu'on le demande spécifiquement.  Si une [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] contient des fichiers multimédia volumineux, configurer ceux\-ci comme fichiers du site d'origine signifie que le lancement de l'application initiale est beaucoup plus rapide, et que les fichiers sont téléchargés uniquement à la demande.  
  
### Configuration des fichiers du site d'origine  
 Si vos fichiers du site d'origine sont inexistants ou inconnus lors de la compilation, vous devez utiliser des mécanismes de déploiement traditionnels pour garantir que les fichiers requis seront disponibles lors de l'exécution, y compris à l'aide du programme de ligne de commande `XCopy` ou de [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Si vous savez lors de la compilation quels fichiers vous aimeriez voir situés sur le site d'origine, mais que vous souhaitez toutefois éviter une dépendance explicite, vous pouvez ajouter ces fichiers à un projet [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] comme élément `None`.  Comme avec les fichiers de contenu, vous devez définir l'attribut [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory` pour spécifier que le fichier du site d'origine est copié vers un emplacement qui est relatif à l'assembly généré, en spécifiant la valeur `Always` ou la valeur `PreserveNewest`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], vous créez un fichier du site d'origine en ajoutant un fichier à un projet et en définissant son `Build Action` à `None`.  
  
 Lorsque le projet est généré, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] copie les fichiers spécifiés dans le dossier de sortie de génération.  
  
### Utilisation de fichiers du site d'origine  
 Pour charger un fichier du site d'origine, vous pouvez appeler la méthode <xref:System.Windows.Application.GetRemoteStream%2A> de la classe <xref:System.Windows.Application>, en passant [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui identifie le fichier du site d'origine souhaité.  <xref:System.Windows.Application.GetRemoteStream%2A> retourne un objet <xref:System.Windows.Resources.StreamResourceInfo>, qui expose le fichier du site d'origine en tant que <xref:System.IO.Stream> et décrit son type de contenu.  
  
 À titre d'exemple, le code suivant montre comment utiliser <xref:System.Windows.Application.GetRemoteStream%2A> pour charger un fichier du site d'origine <xref:System.Windows.Controls.Page> et le définir comme contenu d'un <xref:System.Windows.Controls.Frame> \(`pageFrame`\).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Bien que l'appel de <xref:System.Windows.Application.GetRemoteStream%2A> vous donne accès à <xref:System.IO.Stream>, vous devez exécuter le travail supplémentaire de conversion vers le type de la propriété avec lequel vous le définirez.  À la place, vous pouvez laisser à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] le soin d'ouvrir et de convertir <xref:System.IO.Stream> en chargeant directement un fichier de ressources dans la propriété d'un type à l'aide du code.  
  
 L'exemple suivant montre comment charger directement un <xref:System.Windows.Controls.Page> dans un <xref:System.Windows.Controls.Frame> \(`pageFrame`\) à l'aide du code.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 L'exemple suivant est l'équivalent sous forme de balise de l'exemple précédent.  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## Régénération après modification du type de build  
 Après avoir modifié le type de build d'un fichier de données d'application, vous devez régénérer l'application entière pour vous assurer que ces modifications sont appliquées.  Si vous générez seulement l'application, les modifications ne sont pas appliquées.  
  
## Voir aussi  
 [URI à en\-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)