---
title: "Ressources d&#39;application pour les biblioth&#232;ques qui ciblent des plateformes multiples | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework, ressources lors du ciblage de plateformes multiples"
  - "plateformes multiples, ressources pour"
  - "ressources [.NET Framework]"
  - "ressources, pour plateformes multiples"
  - "ciblage de plateformes multiples, ressources pour"
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
caps.latest.revision: 20
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 20
---
# Ressources d&#39;application pour les biblioth&#232;ques qui ciblent des plateformes multiples
Vous pouvez utiliser le type de projet [Bibliothèque de classes portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) du .NET Framework pour garantir l'accessibilité des ressources de vos bibliothèques de classes à partir de plusieurs plateformes.  Ce type de projet est disponible dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] et cible le sous\-ensemble portable de la bibliothèque de classes du .NET Framework.  L'utilisation de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] garantit l'accessibilité de votre bibliothèque à partir des applications de bureau, des [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], Silverlight et Windows Phone.  
  
 Le projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] ne génère qu'un sous\-ensemble très limité des types dans l'espace de noms <xref:System.Resources> disponible pour votre application, mais il vous permet d'utiliser la classe <xref:System.Resources.ResourceManager> pour extraire des ressources.  Toutefois, si vous créez une application à l'aide de Visual Studio, vous devez utiliser le wrapper fortement typé créé par Visual Studio, plutôt que d'utiliser directement la classe <xref:System.Resources.ResourceManager>.  
  
 Pour créer un wrapper fortement typé dans Visual Studio, définissez le **Modificateur d'accès** du fichier de ressources principal dans le Concepteur de ressources de Visual Studio sur **Public**.  Cela crée un fichier \[resourceFileName\].designer.cs ou \[resourceFileName\].designer.vb qui contient le wrapper fortement typé ResourceManager.  Pour plus d'informations sur l'utilisation d'un wrapper de ressources fortement typé, consultez la section « Génération d'une classe de ressource fortement typée » dans la rubrique [Resgen.exe \(Resource File Generator\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
## Gestionnaire des ressources dans [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]  
 Dans un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], tout accès aux ressources est géré par la classe <xref:System.Resources.ResourceManager>.  Étant donné que les types dans l'espace de noms <xref:System.Resources>, tels que <xref:System.Resources.ResourceReader> et <xref:System.Resources.ResourceSet>, ne sont pas accessibles à partir d'un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], elles ne peuvent pas être utilisées pour accéder aux ressources.  
  
 Le projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] inclut les quatre membres <xref:System.Resources.ResourceManager> répertoriés dans le tableau suivant.  Ces constructeurs et méthodes vous permettent d'instancier un objet <xref:System.Resources.ResourceManager> et d'extraire des ressources de chaîne.  
  
|Membre `ResourceManager`|Description|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Créé une instance <xref:System.Resources.ResourceManager> pour accéder au fichier de ressources nommé trouvé dans l'assembly spécifié.|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Créé une instance <xref:System.Resources.ResourceManager> qui correspond au type spécifié.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Extrait une ressource nommée pour la culture actuelle.|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Extrait une ressource nommée appartenant à la culture spécifiée.|  
  
 L'exclusion d'autres membres <xref:System.Resources.ResourceManager> de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] signifie que les objets sérialisés, les données qui ne sont pas des chaînes, et les images ne peuvent pas être extraits à partir d'un fichier de ressources.  Pour utiliser des ressources à partir de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], vous devez stocker les données d'objet sous forme de chaîne.  Par exemple, vous pouvez stocker des valeurs numériques dans un fichier de ressources en les convertissant en chaînes, et les extraire, puis, vous pouvez les reconvertir en nombres à l'aide de la méthode `Parse` ou `TryParse` du type de données numériques.  Vous pouvez convertir des images ou autres données binaires en représentation sous forme de chaîne en appelant la méthode <xref:System.Convert.ToBase64String%2A?displayProperty=fullName>, et les restaurer en un tableau d'octets en appelant la méthode <xref:System.Convert.FromBase64String%2A?displayProperty=fullName>.  
  
## [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] et Applications Windows Store  
 Les projets [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] stockent des ressources dans des fichiers .resx, qui sont alors compilés dans des fichiers .resources et incorporés dans l'assembly principal ou dans des assemblys satellites au moment de la compilation.  En revanche, les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] requièrent que les ressources soient stockées dans des fichiers .resw, qui sont ensuite compilés dans un seul fichier d'index de ressource de package \(PRI\).  Toutefois, en dépit de formats de fichier incompatibles, le [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] s'exécutera dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
 Pour utiliser votre bibliothèque de classes à partir d'une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ajoutez une référence à celle\-ci dans votre projet d'application Windows Store.  Visual Studio extraira de façon transparente les ressources de l'assembly dans un fichier .resw et les utilisera pour générer un fichier PRI d'où [!INCLUDE[wrt](../../../includes/wrt-md.md)] peut extraire des ressources.  Au moment de l'exécution, [!INCLUDE[wrt](../../../includes/wrt-md.md)] exécute le code dans [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], mais il extrait les ressources de la Bibliothèque de classes portable à partir du fichier PRI.  
  
 Si le projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] inclut des ressources localisées, utilisez le modèle « hub and spoke » pour les déployer comme vous le feriez pour une bibliothèque dans une application de bureau.  Pour utiliser votre fichier de ressources principal et n'importe quel fichier de ressources localisé dans votre application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ajoutez une référence à l'assembly principal.  Au moment de la compilation, Visual Studio extrait les ressources à partir du fichier de ressources principal et de tous les fichiers de ressources localisés dans des fichiers .resw distincts.  Il compile ensuite les fichiers .resw dans un seul fichier PRI pour que le [!INCLUDE[wrt](../../../includes/wrt-md.md)] y accède au moment de l'exécution.  
  
<a name="NonLoc"></a>   
## Exemple : [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] non localisé.  
 L'exemple suivant d'un [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] simple et non localisé utilise des ressources pour stocker les noms des colonnes et déterminer le nombre de caractères à réserver aux données tabulaires.  L'exemple utilise un fichier nommé LibResources.resx pour stocker les ressources de chaîne répertoriées dans le tableau suivant.  
  
|Nom de la ressource|Valeur de la ressource|  
|-------------------------|----------------------------|  
|Né le|Date de naissance|  
|BornLength|12|  
|Embauché|Date d'embauche|  
|HiredLength|12|  
|ID|ID|  
|ID.Length|12|  
|Nom|Nom|  
|NameLength|25|  
|Titre|Base de données des employés|  
  
 Le code suivant définit une classe `UILibrary` qui utilise le wrapper du Gestionnaire des ressources nommé `resources` généré par Visual Studio lorsque le **Modificateur d'accès** du fichier est défini sur **Public**.  La classe UILibrary analyse les données de chaîne selon les besoins.  .  Notez que la classe est dans l'espace de noms `MyCompany.Employees`.  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application en mode console.  Cela nécessite l'ajout d'une référence à UILIbrary.dll au projet d'application console.  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  Cela nécessite l'ajout d'une référence à UILIbrary.dll au projet d'application Windows Store.  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## Exemple : [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] localisé  
 L'exemple de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] localisé suivant inclut des ressources pour les cultures française \(France\) et anglaise \(États\-Unis\).  La culture anglaise \(États\-Unis\) est la culture de l'application par défaut ; ses ressources sont répertoriées dans le tableau de la [section précédente](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc).  Le fichier de ressources de la culture française \(France\) est nommé LibResources.fr\-FR.resx et inclut les ressources de type de chaîne répertoriées dans le tableau suivant.  Le code source de la classe `UILibrary` est identique que celui présenté dans la section précédente.  
  
|Nom de la ressource|Valeur de la ressource|  
|-------------------------|----------------------------|  
|Né le|Date de naissance|  
|BornLength|20|  
|Embauché|Date d'embauche|  
|HiredLength|16|  
|ID|ID|  
|Nom|Nom|  
|Titre|Base de données des employés|  
  
 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application en mode console.  Cela nécessite l'ajout d'une référence à UILIbrary.dll au projet d'application console.  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 Le code suivant illustre de quelle manière la classe `UILibrary` et ses ressources sont accessibles à partir d'une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  Cela nécessite l'ajout d'une référence à UILIbrary.dll au projet d'application Windows Store.  Il utilise la propriété statique `ApplicationLanguages.PrimaryLanguageOverride` pour définir la langue par défaut sur Français.  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## Voir aussi  
 <xref:System.Resources.ResourceManager>   
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)   
 [Empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)