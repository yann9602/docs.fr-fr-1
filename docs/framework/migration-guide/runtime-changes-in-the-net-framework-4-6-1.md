---
title: "Modifications du runtime dans .NET Framework&#160;4.6.1 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifications du runtime .NET Framework"
  - "modifications du runtime .NET Framework 4.6.1"
  - "compatibilité des applications"
ms.assetid: 9d97421c-5fee-4523-98c9-a158e7e6a1ee
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# Modifications du runtime dans .NET Framework&#160;4.6.1
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent les versions antérieures du .NET Framework mais qui s'exécutent sur une version ultérieure du runtime du .NET Framework. Elles incluent également des différences de comportement entre les applications qui s'exécutent sur différents environnements du runtime du .NET Framework. La [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] inclut les modifications apportées dans les domaines suivants :  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Une liaison WCF avec la `TransportWithMessageCredential` mode de sécurité|Par défaut, WCF de liaison qui utilise le `TransportWithMessageCredential` mode de sécurité n’autorise pas de messages avec un unsigned « to » de l’en-tête pour les clés de sécurité asymétrique. Démarrage avec les applications qui s’exécutent sous le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], il est possible d’assouplir cette exigence et recevoir des messages que vous ne faites pas signer les en-têtes « to ».|Il s’agit d’un comportement d’abonnement. Pour autoriser les messages avec unsigned en-têtes « to », ajoutez le paramètre de configuration suivant à la [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :<br /><br /> `<runtime>     <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />  </runtime>`<br /><br /> Parce qu’il s’agit d’une fonctionnalité d’abonnement, le comportement des applications existantes ne devrait pas être affecté.|Bord|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>|Lorsqu’un <xref:System.Windows.Controls.ItemsControl> affiche une collection à l’aide de la virtualisation (<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> = `true`) et élément de défilement (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>), et lorsque le contrôle fait défiler pour afficher un élément dont la hauteur en pixels diffère de ses voisins, le <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> effectue une itération sur tous les éléments dans la collection.   L’interface utilisateur ne répond pas pendant cette itération ;  Si la collection est volumineuse, cela peut être perçu comme un blocage.<br /><br /> Cette itération a lieu dans d’autres circonstances, même dans les versions antérieures à la [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Par exemple, il se produit lors du défilement de pixel (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) lorsqu’il rencontre un élément avec une hauteur en pixels différents et lors du défilement d’élément de données hiérarchiques (comme dans un <xref:System.Windows.Controls.TreeView> contrôle ou une <xref:System.Windows.Controls.ItemsControl> avec regroupement activé) lorsqu’il rencontre un élément avec un nombre différent d’éléments descendants à ses voisins.<br /><br /> Dans le cas de hauteurs des pixels différent et élément de défilement, l’itération a été introduite dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] pour corriger les bogues dans la disposition des données hiérarchiques.  Il n’est pas nécessaire si les données plates (n’a aucune hiérarchie) et le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ne fait pas cela dans ce cas.|Si l’itération a lieu dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] mais pas dans les versions antérieures, autrement dit, si le <xref:System.Windows.Controls.ItemsControl> élément-défile une liste plate avec des éléments de hauteur en pixels différents : il existe deux solutions :<br /><br /> Installer le [.NET Framework 4.6.2](../../../docs/framework/install/guide-for-developers.md).<br /><br /> Installer [correctif HR 1605](https://support.microsoft.com/en-us/kb/3154529) pour la [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].|Secondaire|  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité des applications dans 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)