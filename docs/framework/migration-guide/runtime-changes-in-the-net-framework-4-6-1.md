---
title: "Modification du runtime dans le .NET Framework 4.6.1 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 9d97421c-5fee-4523-98c9-a158e7e6a1ee
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b8c6ec4d0bad4a769fb4d19a98c9e8a4eda0db78
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-461"></a>Modifications du runtime dans le .NET Framework 4.6.1
Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent les versions antérieures du .NET Framework mais qui s'exécutent sur une version ultérieure du runtime du .NET Framework. Elles incluent également des différences de comportement entre les applications qui s'exécutent sur différents environnements du runtime du .NET Framework. Dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], des modifications ont été apportées au niveau de :  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|Liaison WCF avec le mode de sécurité `TransportWithMessageCredential`|Par défaut, une liaison WCF qui utilise le mode de sécurité `TransportWithMessageCredential` n’autorise pas les messages avec un en-tête « to » non signé pour les clés de sécurité asymétriques. À compter des applications qui s’exécutent dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], il est possible d’assouplir cette exigence et de recevoir des messages sans en-tête « to » signé.|Il s’agit d’un comportement d’abonnement. Pour autoriser les messages avec des en-têtes « to » non signés, ajoutez le paramètre de configuration suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :<br /><br /> `<runtime>     <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />  </runtime>`<br /><br /> Parce qu’il s’agit d’une fonctionnalité d’abonnement, le comportement des applications existantes ne devrait pas être affecté.|Limité|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|Fonctionnalité|Modification|Impact|Portée|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>|Lorsqu’un <xref:System.Windows.Controls.ItemsControl> affiche une collection à l’aide de la virtualisation (<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> = `true`) et du défilement des éléments (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>), et lorsque le contrôle fait défiler la vue pour afficher un élément dont la hauteur en pixels diffère de celle de ses voisins, le <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> effectue une itération sur tous les éléments de la collection.   L’interface utilisateur ne répond pas pendant cette itération. Si la collection est volumineuse, vous pouvez avoir l’impression que l’application ne répond plus.<br /><br /> Cette itération a lieu dans d’autres circonstances, même dans les versions antérieures au [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Par exemple, elle se produit lors du défilement de pixels (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>), lorsqu’elle rencontre un élément avec une hauteur en pixels différente, et lors du défilement des éléments de données hiérarchiques (comme dans un contrôle <xref:System.Windows.Controls.TreeView> ou <xref:System.Windows.Controls.ItemsControl> avec le regroupement activé), lorsqu’elle rencontre un élément avec un nombre d’éléments descendants différent de celui de ses voisins.<br /><br /> Dans le cas d’un défilement d’éléments et de hauteurs de pixels différentes, l’itération a été ajoutée au [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] pour corriger les bogues au niveau de la disposition des données hiérarchiques.  Elle n’est pas nécessaire si les données sont plates (c’est-à-dire qu’elles n’ont pas de hiérarchie). Le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ne l’exécute donc pas dans ce cas.|Si l’itération a lieu dans le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], mais pas dans les versions antérieures (c’est-à-dire que <xref:System.Windows.Controls.ItemsControl> effectue le défilement d’éléments d’une liste plate comportant des éléments de hauteurs en pixels différentes), vous avez deux solutions :<br /><br /> Installer le [.NET Framework 4.6.2](../../../docs/framework/install/guide-for-developers.md)<br /><br /> Installer le [correctif HR 1605](https://support.microsoft.com/en-us/kb/3154529) pour le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|Mineur|  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité des applications dans la version 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
