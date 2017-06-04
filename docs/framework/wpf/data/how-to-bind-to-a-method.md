---
title: "Comment&#160;: effectuer une liaison &#224; une m&#233;thode | Microsoft Docs"
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
  - "liaison, à des méthodes"
  - "classes, ObjectDataProvider"
  - "liaison de données, lier à des méthodes à l'aide de ObjectDataProvider"
  - "méthodes, lier à"
  - "ObjectDataProvider (classe)"
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: effectuer une liaison &#224; une m&#233;thode
L'exemple suivant indique comment créer une liaison avec une méthode à l'aide de <xref:System.Windows.Data.ObjectDataProvider>.  
  
## Exemple  
 Dans cet exemple, `TemperatureScale` est une classe qui a une méthode `ConvertTemp`, qui prend deux paramètres \(un de type `double` et un de type `enum``TempType)`\) et convertit la valeur donnée d'une échelle de température à une autre.  Dans l'exemple suivant, un <xref:System.Windows.Data.ObjectDataProvider> est utilisé pour instancier l'objet `TemperatureScale`.  La méthode `ConvertTemp` est appelée avec deux paramètres spécifiés.  
  
 [!code-xml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 Maintenant que la méthode est disponible en tant que ressource, vous pouvez créer une liaison avec ses résultats.  Dans l'exemple suivant, la propriété <xref:System.Windows.Controls.TextBox.Text%2A> du <xref:System.Windows.Controls.TextBox> et le <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> du <xref:System.Windows.Controls.ComboBox> est liée aux deux paramètres de la méthode.  Cela permet aux utilisateurs de spécifier la température sur et à partir de laquelle effectuer la conversion.  Notez que <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> a la valeur `true` car nous créons une liaison avec la propriété <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> de l'instance <xref:System.Windows.Data.ObjectDataProvider> et pas avec les propriétés de l'objet encapsulé par le <xref:System.Windows.Data.ObjectDataProvider> \(l'objet `TemperatureScale`\).  
  
 Le <xref:System.Windows.Controls.ContentControl.Content%2A> du dernier <xref:System.Windows.Controls.Label> se met à jour lorsque l'utilisateur modifie le contenu du <xref:System.Windows.Controls.TextBox> ou la sélection du <xref:System.Windows.Controls.ComboBox>.  
  
 [!code-xml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 Le convertisseur `DoubleToString` prend un double et le transforme en chaîne dans la direction <xref:System.Windows.Data.IValueConverter.Convert%2A> \(de la [source de liaison](GTMT) à [la cible de liaison](GTMT), qui est la propriété <xref:System.Windows.Controls.TextBox.Text%2A>\) et convertit un `string` en `double` dans la direction <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.  
  
 La `InvalidationCharacterRule` est une <xref:System.Windows.Controls.ValidationRule> qui vérifie les caractères non valides.  Le modèle d'erreur par défaut, qui est une bordure rouge autour du <xref:System.Windows.Controls.TextBox> semble notifier les utilisateurs lorsque la valeur d'entrée n'est pas une valeur double.  
  
## Voir aussi  
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [Effectuer une liaison à une énumération](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)