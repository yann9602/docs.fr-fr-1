---
title: "Dictionnaires de ressources fusionn&#233;s | Microsoft Docs"
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
  - "dictionnaires de ressources fusionnés"
  - "dictionnaires de ressources fusionnés"
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Dictionnaires de ressources fusionn&#233;s
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ressources prennent en charge une fonctionnalité de dictionnaire de ressources fusionnés. Cette fonctionnalité fournit un moyen de définir la partie ressources d’une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application en dehors de la compilation [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] application. Les ressources peuvent ensuite être partagées entre les applications et sont également plus facilement isolées pour la localisation.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Présentation d’un dictionnaire de ressources fusionnés  
 Dans le balisage, vous utilisez la syntaxe suivante pour introduire un dictionnaire de ressources fusionné dans une page :  
  
 [!code-xml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Notez que la <xref:System.Windows.ResourceDictionary> élément n’a pas une [x : Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), qui est généralement nécessaire pour tous les éléments dans une collection de ressources. Alors qu’un autre <xref:System.Windows.ResourceDictionary> de référence dans le <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection est un cas particulier, réservé pour ce scénario de dictionnaire de ressources fusionnés. Le <xref:System.Windows.ResourceDictionary> qui présente une fusion dictionnaire de ressources ne peut pas avoir un [x : Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md). En général, chaque <xref:System.Windows.ResourceDictionary> dans les <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection spécifie un <xref:System.Windows.ResourceDictionary.Source%2A> attribut. La valeur de <xref:System.Windows.ResourceDictionary.Source%2A> doit être un [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] qui correspond à l’emplacement du fichier de ressources à fusionner. La destination [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] doit être un autre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier, avec <xref:System.Windows.ResourceDictionary> comme élément racine.  
  
> [!NOTE]
>  Il est permis de définir des ressources dans un <xref:System.Windows.ResourceDictionary> qui est spécifié comme un dictionnaire fusionné, soit comme alternative à la spécification <xref:System.Windows.ResourceDictionary.Source%2A>, ou en plus des ressources incluses à partir de la source spécifiée. Toutefois, cela n’est pas un scénario courant ; le scénario principal pour les dictionnaires fusionnés consiste à fusionner des ressources à partir des emplacements de fichier externe. Si vous souhaitez spécifier des ressources dans le balisage d’une page, vous devez généralement définir principal <xref:System.Windows.ResourceDictionary> et non dans les dictionnaires fusionnés.  
  
## <a name="merged-dictionary-behavior"></a>Comportement de dictionnaire fusionné  
 Ressources d’un dictionnaire fusionné occupent un emplacement dans l’étendue de recherche de ressource qui se trouve juste après la portée du dictionnaire de ressources principal qu’elles sont fusionnées dans. Bien qu’une clé de ressource doit être unique au sein d’un dictionnaire individuel, une clé peut contenir plusieurs fois dans un ensemble de dictionnaires fusionnés. Dans ce cas, la ressource retournée proviendra du dernier dictionnaire trouvé de manière séquentielle dans le <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection. Si le <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection a été définie dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], l’ordre des dictionnaires fusionnés de la collection est l’ordre des éléments fournis dans le balisage. Si une clé est définie dans le dictionnaire principal et également dans un dictionnaire qui a été fusionné, puis la ressource retournée proviendra du dictionnaire principal. Ces règles de portée s’appliquent également à la fois les références de ressources statiques et dynamiques pour les références.  
  
### <a name="merged-dictionaries-and-code"></a>Dictionnaires fusionnés et Code  
 Les dictionnaires fusionnés peuvent être ajoutés à un `Resources` dictionnaire via le code. La valeur par défaut, initialement vide <xref:System.Windows.ResourceDictionary> qui existe pour `Resources` propriété possède également une valeur par défaut, initialement vide <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> propriété de collection. Pour ajouter un dictionnaire fusionné dans le code, vous obtenir une référence vers le principal souhaité <xref:System.Windows.ResourceDictionary>, obtenir sa <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> valeur de propriété et appelez `Add` sur le générique `Collection` qui est contenue dans <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. L’objet que vous ajoutez doit être un nouveau <xref:System.Windows.ResourceDictionary>. Dans le code, vous ne définissez pas la <xref:System.Windows.ResourceDictionary.Source%2A> propriété. Au lieu de cela, vous devez obtenir un <xref:System.Windows.ResourceDictionary> objet en créant une ou du chargement d’une. Une façon de charger un <xref:System.Windows.ResourceDictionary> pour appeler <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName> une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flux de fichier qui a un <xref:System.Windows.ResourceDictionary> racine, puis effectuer un cast du <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName> retourner la valeur à <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>URI de dictionnaire de ressources fusionnés  
 Il existe plusieurs techniques pour inclure un dictionnaire de ressources fusionné, indiquées par le [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] format que vous allez utiliser. De manière générale, ces techniques peuvent être divisées en deux catégories : ressources qui sont compilés dans le cadre du projet et les ressources qui ne sont pas compilées dans le cadre du projet.  
  
 Pour les ressources qui sont compilés dans le cadre du projet, vous pouvez utiliser un chemin d’accès relatif qui fait référence à l’emplacement de la ressource. Le chemin d’accès relatif est évalué pendant la compilation. Votre ressource doit être définie dans le cadre du projet comme une action de génération ressource. Si vous incluez un fichier .xaml de ressources dans le projet en tant que ressource, vous n’avez pas besoin de copier le fichier de ressources dans le répertoire de sortie, la ressource est déjà incluse dans l’application compilée. Vous pouvez utiliser également l’action de génération contenu, mais vous devez ensuite copier les fichiers dans le répertoire de sortie et également déployer les fichiers de ressources dans la même relation de chemin d’accès au fichier exécutable.  
  
> [!NOTE]
>  N’utilisez pas l’action de génération ressource incorporée. L’action de génération elle-même est prise en charge pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des applications, mais la résolution de <xref:System.Windows.ResourceDictionary.Source%2A> n’incorpore pas <xref:System.Resources.ResourceManager>et ne peut donc pas séparer la ressource individuelle du flux. Vous pouvez toujours utiliser ressource incorporée pour d’autres applications dans la mesure où vous avez également utilisé <xref:System.Resources.ResourceManager> pour accéder aux ressources.  
  
 Une technique similaire consiste à utiliser un URI à en-tête Pack à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier et y faire référence en comme Source. URI à en-tête pack active des références aux composants d’assemblys référencés et d’autres techniques. Pour plus d’informations sur les URI à en-tête Pack, consultez [ressource d’Application WPF, de contenu et les fichiers de données](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pour les ressources qui ne sont pas compilées dans le cadre du projet, l’URI est évaluée au moment de l’exécution. Vous pouvez utiliser un transport d’URI courant comme fichier : ou http : pour faire référence au fichier de ressources. L’inconvénient de l’utilisation de l’approche de ressource non compilée est ce fichier : nécessite l’accès http et les étapes de déploiement supplémentaires : accès implique la zone de sécurité Internet.  
  
### <a name="reusing-merged-dictionaries"></a>Réutilisation des dictionnaires fusionnés  
 Vous pouvez réutiliser ou partager les dictionnaires de ressources entre les applications, car le dictionnaire de ressources à fusionner peut être référencé via valide [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Exactement la procédure à suivre dépend de votre stratégie de déploiement d’application et modèle d’application suivent. La stratégie d’URI à en-tête Pack mentionné ci-dessus fournit un moyen de se procurer couramment une ressource fusionnée dans plusieurs projets lors du développement en partageant une référence d’assembly. Dans ce cas les ressources sont toujours distribuées par le client et au moins une des applications doit déployer l’assembly référencé. Il est également possible de référencer des ressources fusionnées via un URI distribué qui utilise le protocole http.  
  
 Écriture de dictionnaires fusionnés comme application locale des fichiers ou à un stockage partagé local est un autre dictionnaire fusionné possible / scénario de déploiement d’application.  
  
### <a name="localization"></a>Localisation  
 Si les ressources à localiser sont isolées dans des dictionnaires qui sont fusionnés dans des dictionnaires primaires et conservées sous forme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ces fichiers peuvent être localisés séparément. Cette technique est une alternative légère à la localisation des assemblys de ressources satellites. Pour plus d’informations, consultez [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.ResourceDictionary>   
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Ressources et Code](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [Ressource d’Application WPF, de contenu et les fichiers de données](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)