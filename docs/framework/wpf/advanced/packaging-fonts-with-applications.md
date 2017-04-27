---
title: "Empaquetage de polices avec des applications | Microsoft Docs"
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
  - "applications, empaqueter des polices avec"
  - "polices, empaqueter avec des applications"
  - "empaqueter des polices avec des applications"
  - "typographie, empaqueter des polices avec des applications"
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Empaquetage de polices avec des applications
Cette rubrique fournit une vue d'ensemble de la manière d'empaqueter des polices avec votre application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
> [!NOTE]
>  Comme avec la plupart des types de logiciels, les fichiers de police font l'objet d'une licence et ne sont pas vendus.  Les licences qui régissent l'utilisation de polices varient d'un fournisseur à l'autre mais en général, la plupart des licences \(y compris celles qui portent sur des polices [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)]\) fournies avec des applications et [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], n'autorisent pas l'incorporation de polices dans des applications ni leur redistribution.  Par conséquent, en tant que développeur, il vous incombe de veiller à disposer des droits de licence requis pour toute police incorporée dans une application ou redistribuée d'une autre manière.  
  
   
  
<a name="introduction_to_packaging_fonts"></a>   
## Introduction à l'empaquetage de polices  
 Vous pouvez empaqueter facilement des polices comme ressources dans vos applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour afficher le texte de l'interface utilisateur et d'autres types de contenu basé sur du texte.  Les polices peuvent être séparées des fichiers d'assembly de l'application ou y être incorporées.  Vous pouvez également créer une typothèque de ressources uniquement, que votre application peut référencer.  
  
 Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] et [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] contiennent un indicateur de type \(fsType\) qui indique les droits de licence pour incorporation de la police.  Toutefois, cet indicateur de type fait seulement référence aux polices incorporées stockées dans un document. Il ne fait pas référence aux polices incorporées dans une application.  Vous pouvez récupérer les droits d'incorporation de polices pour une police en créant un objet <xref:System.Windows.Media.GlyphTypeface> et en référençant sa propriété <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>.  Pour plus d'informations sur l'indicateur fsType, reportez\-vous à la section « OS\/2 and Windows Metrics » de la page [OpenType Specification](http://www.microsoft.com/typography/otspec/os2.htm).  
  
 Le site Web sur la [typographie de Microsoft](http://www.microsoft.com/typography/links/) inclut des informations de contact qui peuvent vous aider à localiser un fournisseur de polices ou à trouver un fournisseur de polices pour un projet particulier.  
  
<a name="adding_fonts_as_content_items"></a>   
## Ajout de polices en tant qu'éléments de contenu  
 Vous pouvez ajouter des polices à votre application en tant qu'éléments de contenu du projet distincts des fichiers d'assembly de l'application.  Cela signifie que les éléments de contenu ne sont pas incorporés comme ressources dans un assembly.  L'exemple de fichier projet suivant indique comment définir des éléments de contenu.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 Pour garantir que l'application peut utiliser les polices au moment de l'exécution, ces polices doivent être accessibles dans le répertoire de déploiement de l'application.  L'élément `<CopyToOutputDirectory>` du fichier projet de l'application vous permet de copier automatiquement les polices vers le répertoire de déploiement de l'application pendant le processus de génération.  L'exemple de fichier projet suivant indique comment copier des polices vers le répertoire de déploiement.  
  
```  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 L'exemple de code suivant indique comment référencer la police de l'application comme élément de contenu. L'élément de contenu référencé doit se trouver dans le même répertoire que les fichiers d'assembly de l'application.  
  
 [!code-xml[FontSnippets#FontPackageSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## Ajout de polices en tant qu'éléments de ressource  
 Vous pouvez ajouter des polices à votre application comme éléments de ressource du projet qui sont incorporés dans les fichiers d'assembly de l'application.  L'utilisation d'un sous\-répertoire distinct pour les ressources permet d'organiser les fichiers projet de l'application.  L'exemple de fichier projet suivant indique comment définir des polices comme éléments de ressource dans un sous\-répertoire séparé.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  Lorsque vous ajoutez des polices comme ressources à votre application, assurez\-vous que vous définissez l'élément `<Resource>`, et non l'élément `<EmbeddedResource>` dans le fichier projet de votre application.  L'élément `<EmbeddedResource>` de l'action de génération n'est pas pris en charge.  
  
 L'exemple de balisage suivant indique comment référencer les ressources de police de l'application.  
  
 [!code-xml[FontSnippets#FontPackageSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### Référencement d'éléments de ressource de police dans le code  
 Pour référencer des éléments de ressource de police à partir du code, vous devez fournir une référence à une ressource de police en deux parties : le [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de base et la référence de l'emplacement de la police.  Ces valeurs sont utilisées comme paramètres pour la méthode <xref:System.Windows.Media.FontFamily.%23ctor%2A>.  L'exemple de code suivant montre comment référencer les ressources de police de l'application dans le sous\-répertoire de projet appelé `resources`.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 Le [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de base peut inclure le sous\-répertoire d'application où la ressource de police réside.  Dans ce cas, la référence de l'emplacement de la police ne doit pas spécifier de répertoire, mais doit inclure un préfixe `./`, qui indique que la ressource de police se trouve dans le même répertoire spécifié par le [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de base.  L'exemple de code suivant montre une autre manière de référencer l'élément de ressource de police. Il équivaut à l'exemple de code précédent.  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### Référencement de polices à partir du même sous\-répertoire d'application  
 Vous pouvez placer les fichiers de contenu d'application et les fichiers de ressources dans le même sous\-répertoire défini par l'utilisateur dans votre projet d'application.  L'exemple de fichier projet suivant montre une page de contenu et des ressources de police définies dans le même sous\-répertoire.  
  
```  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 Comme le contenu de l'application et la police se trouvent dans le même sous\-répertoire, la référence de police est relative au contenu d'application.  Les exemples suivants indiquent comment référencer la ressource de police de l'application lorsque la police se trouve dans le même répertoire que l'application.  
  
 [!code-xml[FontSnippets#FontPackageSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### Énumération des polices dans une application  
 Pour énumérer des polices en tant qu'éléments de ressource dans votre application, utilisez la méthode <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> ou <xref:System.Windows.Media.Fonts.GetTypefaces%2A>.  L'exemple suivant montre comment utiliser la méthode <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> pour renvoyer la collection d'objets <xref:System.Windows.Media.FontFamily> depuis l'emplacement des polices de l'application.  Dans ce cas, l'application contient un sous\-répertoire appelé « ressources ».  
  
 [!code-csharp[FontSnippets#FontsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 L'exemple suivant montre comment utiliser la méthode <xref:System.Windows.Media.Fonts.GetTypefaces%2A> pour renvoyer la collection d'objets <xref:System.Windows.Media.Typeface> depuis l'emplacement des polices de l'application.  Dans ce cas, l'application contient un sous\-répertoire appelé « ressources ».  
  
 [!code-csharp[FontSnippets#FontsSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## Création d'une bibliothèque de ressources de polices  
 Vous pouvez créer une bibliothèque de ressources uniquement qui ne contient que des polices. Ce type de projet de bibliothèque ne renferme aucun code.  La création d'une bibliothèque de ressources uniquement est une technique fréquemment utilisée pour découpler des ressources du code d'application qui les utilise.  L'assembly de bibliothèque peut ainsi être inclus dans plusieurs projets d'application.  L'exemple de fichier projet suivant montre les parties clés d'un projet de bibliothèque contenant uniquement des ressources.  
  
```  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### Référencement d'une police dans une bibliothèque de ressources  
 Pour référencer une police dans une bibliothèque de ressources de votre application, vous devez faire précéder la référence de police du nom de l'assembly de bibliothèque.  Dans le cas présent, l'assembly de ressource de police est « FontLibrary ».  Pour séparer le nom de l'assembly de la référence dans l'assembly, utilisez un caractère ';'.  L'ajout du mot clé « Component » suivi de la référence au nom de police complète la référence à la ressource du typothèque.  L'exemple de code suivant indique comment référencer une police dans un assembly de bibliothèque de ressources.  
  
 [!code-xml[OpenTypeFontsSample#OpenTypeFontsSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  Ce Kit de développement logiciel contient un jeu des exemples de polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] que vous pouvez utiliser avec les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Les polices sont définies dans une bibliothèque de ressources uniquement.  Pour plus d'informations, consultez [Exemple de pack de polices OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
<a name="limitations_on_font_usage"></a>   
## Limitations sur l'utilisation de polices  
 La liste suivante décrit plusieurs restrictions sur l'empaquetage et l'utilisation de polices dans les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
-   **Bits d'autorisation d'incorporation de polices :** les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne vérifient ni n'appliquent les bits d'autorisation d'incorporation de polices.  Consultez la section [Introduction à l'empaquetage de polices](#introduction_to_packaging_fonts) pour plus d'informations.  
  
-   **Site de polices d'origine :** les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n'autorisent pas de référence de police à un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] http ou ftp.  
  
-   **URI absolu utilisant la notation « pack: » :** les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne vous permettent pas de créer par programme un objet <xref:System.Windows.Media.FontFamily> utilisant la notation « pack: » dans le cadre de la référence [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] absolue à une police.  Par exemple, `"pack://application:,,,/resources/#Pericles Light"` est une référence de police non valide.  
  
-   **Incorporation de police automatique :** Au moment du design, la recherche des polices utilisées par une application et l'incorporation automatique des polices dans les ressources de l'application ne sont pas prises en charge.  
  
-   **Sous\-ensembles de polices :** les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne prennent pas en charge la création de sous\-ensembles de polices pour les documents non fixes.  
  
-   En cas de référence incorrecte, l'application retourne à une police disponible.  
  
## Voir aussi  
 <xref:System.Windows.Documents.Typography>   
 <xref:System.Windows.Media.FontFamily>   
 [Typographie Microsoft : Liens, nouvelles et contacts \(page éventuellement en anglais\)](http://www.microsoft.com/typography/links/)   
 [Spécification OpenType \(page éventuellement en anglais\)](http://www.microsoft.com/typography/otspec/)   
 [Fonctionnalités des polices OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)   
 [Exemple de pack de polices OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)