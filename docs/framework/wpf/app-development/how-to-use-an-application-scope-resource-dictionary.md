---
title: "Comment&#160;: utiliser un dictionnaire de ressources de port&#233;e application | Microsoft Docs"
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
  - "dictionnaire de ressources de portée application"
  - "dictionnaires, ressource"
  - "dictionnaires de ressources, de portée application"
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: utiliser un dictionnaire de ressources de port&#233;e application
Cet exemple indique comment définir et utiliser un dictionnaire de ressources personnalisé de portée application.  
  
## Exemple  
 <xref:System.Windows.Application> expose un magasin de portée d'application pour les ressources partagées : <xref:System.Windows.Application.Resources%2A>.  Par défaut, la propriété <xref:System.Windows.Application.Resources%2A> est initialisée avec une instance du type <xref:System.Windows.ResourceDictionary>.  Vous utilisez cette instance lorsque vous obtenez et définissez des propriétés de portée application à l'aide de <xref:System.Windows.Application.Resources%2A>.  \(Pour plus d'informations, consultez [How to: Get and Set an Application\-Scope Resource](http://msdn.microsoft.com/fr-fr/39e0420c-c9fc-47dc-8956-fdd95b214095)\).  
  
 Si vous disposez des plusieurs ressources que vous définissez à l'aide de <xref:System.Windows.Application.Resources%2A>, vous pouvez utiliser à la place un dictionnaire de ressources personnalisé pour stocker ces ressources et vous en servir à la place pour définir <xref:System.Windows.Application.Resources%2A>.  Les éléments suivants indiquent comment vous déclarez un dictionnaire de ressources personnalisé à l'aide de XAML.  
  
 [!code-xml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 L'échange de dictionnaires de ressources entiers à l'aide de <xref:System.Windows.Application.Resources%2A> vous permet de prendre en charge des thèmes de portée application, où chaque thème est encapsulé par un dictionnaire de ressources unique.  L'exemple suivant montre comment définir <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 Les éléments suivants indiquent comment vous pouvez obtenir des ressources de portée application du dictionnaire de ressources exposé par <xref:System.Windows.Application.Resources%2A> en XAML.  
  
 [!code-xml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 Les éléments suivants indiquent comment vous pouvez également placer les ressources dans le code.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Il existe deux considérations à prendre en compte lors de l'utilisation de <xref:System.Windows.Application.Resources%2A>.  En premier lieu, la *clé* de dictionnaire est un objet, donc vous devez utiliser exactement la même instance de l'objet lorsque vous définissez et obtenez une valeur de propriété.  \(Notez que la clé respecte la casse lors de l'utilisation d'une chaîne.\) En second lieu, la *valeur* de dictionnaire est un objet, donc vous devrez convertir la valeur en type souhaité lors de l'obtention d'une valeur de propriété.  
  
## Voir aussi  
 <xref:System.Windows.ResourceDictionary>   
 <xref:System.Windows.Application.Resources%2A>   
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Dictionnaires de ressources fusionnés](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)