---
title: "D&#233;finition d&#39;une propri&#233;t&#233; dans les contr&#244;les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles personnalisés (Windows Forms), définir les propriétés dans le code"
  - "propriétés (Windows Forms), définir dans le code"
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# D&#233;finition d&#39;une propri&#233;t&#233; dans les contr&#244;les Windows Forms
Pour une vue d'ensemble des propriétés, consultez [Properties Overview](../Topic/Properties%20Overview.md).  Vous devez tenir compte de certaines remarques importantes lors de la définition d'une propriété :  
  
-   Vous devez appliquer des attributs aux propriétés que vous définissez.  Les attributs spécifient la manière dont le concepteur doit afficher une propriété.  Pour plus d'informations, consultez [Design\-Time Attributes for Components](../Topic/Design-Time%20Attributes%20for%20Components.md).  
  
-   Si la modification de la propriété affecte l'affichage du contrôle, appelez la méthode <xref:System.Windows.Forms.Control.Invalidate%2A> \(que votre contrôle hérite de <xref:System.Windows.Forms.Control>\) de l'accesseur `set`.  <xref:System.Windows.Forms.Control.Invalidate%2A> appelle alors la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>, redessinant ainsi le contrôle.  Plusieurs appels à <xref:System.Windows.Forms.Control.Invalidate%2A> entraînent un appel unique à <xref:System.Windows.Forms.Control.OnPaint%2A> pour davantage d'efficacité.  
  
-   La bibliothèque de classes .NET Framework fournit des convertisseurs de type pour les types de données courants, tels que les entiers, les nombres décimaux, les valeurs booléennes, etc.  Un convertisseur de type a généralement pour objectif de convertir une chaîne en valeur \(des données de type chaîne en autres types de données\).  Les types de données courants sont associés aux convertisseurs de type par défaut qui convertissent des valeurs en chaînes et des chaînes en types de données appropriés.  Si vous définissez une propriété de type de données personnalisé \(c'est\-à\-dire non standard\), vous devez appliquer un attribut qui spécifie le convertisseur de type à associer à cette propriété.  Vous pouvez également utiliser un attribut pour associer un éditeur de types muni d'une interface utilisateur personnalisé à une propriété.  Un éditeur de types muni d'une interface utilisateur fournit une interface utilisateur pour la modification d'une propriété ou d'un type de données.  Un sélecteur de couleur constitue un exemple d'éditeur de types muni d'une interface utilisateur.  Vous trouverez des exemples d'attributs à la fin de cette rubrique.  
  
    > [!NOTE]
    >  Si aucun convertisseur de type ou éditeur de types muni d'une interface utilisateur n'est disponible pour votre propriété personnalisée, vous pouvez en implémenter un comme décrit dans [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md).  
  
 Le fragment de code suivant définit une propriété personnalisée appelée `EndColor` pour le contrôle personnalisé `FlashTrackBar`.  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 Le fragment de code suivant associe un convertisseur de type et un éditeur de types muni d'une interface utilisateur à la propriété `Value`.  Dans ce cas, `Value` est un entier et possède un convertisseur de type par défaut, mais l'attribut <xref:System.ComponentModel.TypeConverterAttribute> applique un convertisseur de type personnalisé \(`FlashTrackBarValueConverter`\) qui permet au concepteur de l'afficher sous la forme d'un pourcentage.  L'éditeur de types muni d'une interface utilisateur, `FlashTrackBarValueEditor`, permet d'afficher le pourcentage.  Cet exemple montre également que le convertisseur de type ou l'éditeur spécifié par l'attribut <xref:System.ComponentModel.TypeConverterAttribute> ou <xref:System.ComponentModel.EditorAttribute> substitue le convertisseur par défaut.  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## Voir aussi  
 [Propriétés dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)   
 [Événements de modification de propriété](../../../../docs/framework/winforms/controls/property-changed-events.md)   
 [Attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)