---
title: "Utilisation de la Biblioth&#232;que de classes portable avec le mod&#232;le d&#39;affichage Mod&#232;le-Affichage | Microsoft Docs"
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
  - "Bibliothèque de classes portable [.NET Framework], et MVVM"
  - "MVVM, et bibliothèque de classes portable"
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Utilisation de la Biblioth&#232;que de classes portable avec le mod&#232;le d&#39;affichage Mod&#232;le-Affichage
Vous pouvez utiliser .NET Framework [Bibliothèque de classes portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) pour implémenter le modèle de \(MVVM\) de modèle de Modèle\-Vue\- afficher et de partager les assemblys entre les plates\-formes multiples.  
  
 MVVM est un modèle d'application qui isole l'interface utilisateur de la logique métier sous\-jacente.  Vous pouvez implémenter des classes de modèle et de modèle vue dans un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], puis créer des vues qui sont personnalisées pour des plateformes.  Cette approche vous permet d'écrire le modèle de données et la logique métier une seule fois, et utilise ce code des applications .NET Framework, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Silverlight, de téléphone Windows, et Windows, comme indiqué dans l'illustration suivante.  
  
 ![Portable avec diagramme MVVM](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 Cette rubrique ne fournit pas les informations générales à propos du modèle MVVM.  Il fournit uniquement des informations sur l'utilisation [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] pour implémenter MVVM.  Pour plus d'informations sur la bibliothèque d'agents asynchrones, consultez [MVVM Quickstart](http://go.microsoft.com/fwlink/?LinkId=234934) dans la bibliothèque MSDN.  
  
## Classes qui prennent en charge MVVM  
 Lorsque vous ciblez [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, ou Windows phone 7.5 pour votre projet de [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], les classes suivantes sont disponibles pour implémenter le modèle MVVM :  
  
-   Classe <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=fullName>  
  
-   Classe <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=fullName>  
  
-   Classe <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=fullName>  
  
-   Classe <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=fullName>  
  
-   Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=fullName>  
  
-   Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=fullName>  
  
-   Classe <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=fullName>  
  
-   Classe <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=fullName>  
  
-   Classe <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=fullName>  
  
-   Classe <xref:System.Windows.Input.ICommand?displayProperty=fullName>  
  
-   Toutes les classes dans l'espace de noms <xref:System.ComponentModel.DataAnnotations?displayProperty=fullName>  
  
## implémenter MVVM  
 Pour implémenter MVVM, vous créez en général le modèle et le modèle de vue dans un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], car un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] ne peut pas référencer un projet non portables.  Le modèle et le modèle de vue peuvent se trouver dans le même projet ou dans des projets séparés.  Si vous utilisez des projets séparés, ajoutez une référence de projet de modèle de vue au projet de modèle.  
  
 Une fois que vous avez compilé les projets de modèle et de vue, vous référencez ces assemblys dans l'application qui contient la vue.  Si la vue interagit avec uniquement le modèle vue, vous devez référencer l'assembly qui contient le modèle de vue.  
  
### Modèle  
 L'exemple suivant montre une classe de modèle simplifiée qui peut résider dans un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)].  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 L'exemple suivant illustre une méthode simple pour remplir, récupérer, et mettre à jour les données dans un projet [!INCLUDE[net_portable](../../../includes/net-portable-md.md)].  Dans une application réelle, vous extrairiez les données d'une source comme un service Windows Communication Foundation \(WCF\).  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### Vue du modèle  
 Une classe de base pour les modèles de vue est souvent ajoutée lorsque vous implémentez le modèle MVVM.  L'exemple suivant montre une classe de base.  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 Une implémentation de l'interface d' <xref:System.Windows.Input.ICommand> est fréquemment utilisée avec le modèle MVVM.  L'exemple suivant illustre une implémentation de l'interface <xref:System.Windows.Input.ICommand>.  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 L'exemple suivant illustre un modèle de vue simplifiée.  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### Vue  
 D'une application d' [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], l'application d' [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], Silverlight est basé sur l'application, ou Windows phone l'application 7.5, vous pouvez référencer l'assembly qui contient les projets de modèle et de vue.  Vous créez ensuite une vue qui interagit avec le modèle de vue.  L'exemple suivant montre une application simplifiée de Windows Presentation Foundation \(WPF\) qui récupère et met à jour les données du modèle de vue.  Vous pouvez créer des vues similaires dans Silverlight, Windows phone, ou des applications d' [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
 [!code-xml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## Voir aussi  
 [Bibliothèque de classes portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)