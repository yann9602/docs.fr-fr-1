---
title: "Définition d'une propriété dans les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c3c25b9c408e5b8f0b76cdf87375875cdb06a13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="defining-a-property-in-windows-forms-controls"></a><span data-ttu-id="db6c1-102">Définition d'une propriété dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db6c1-102">Defining a Property in Windows Forms Controls</span></span>
<span data-ttu-id="db6c1-103">Vous trouverez une vue d’ensemble de propriétés sur la page [Vue d’ensemble des propriétés](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="db6c1-103">For an overview of properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="db6c1-104">Il est important de prendre en compte plusieurs points avant de définir une propriété :</span><span class="sxs-lookup"><span data-stu-id="db6c1-104">There are a few important considerations when defining a property:</span></span>  
  
-   <span data-ttu-id="db6c1-105">Vous devez appliquer des attributs aux propriétés que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="db6c1-105">You must apply attributes to the properties you define.</span></span> <span data-ttu-id="db6c1-106">Les attributs spécifient la manière dont le concepteur doit afficher une propriété.</span><span class="sxs-lookup"><span data-stu-id="db6c1-106">Attributes specify how the designer should display a property.</span></span> <span data-ttu-id="db6c1-107">Pour plus d’informations, consultez la page [Attributs au moment du design des composants](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="db6c1-107">For details, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
-   <span data-ttu-id="db6c1-108">Si la modification de la propriété affecte l’affichage visuel du contrôle, appelez le <xref:System.Windows.Forms.Control.Invalidate%2A> (méthode) (qui hérite de votre contrôle <xref:System.Windows.Forms.Control>) à partir de la `set` accesseur.</span><span class="sxs-lookup"><span data-stu-id="db6c1-108">If changing the property affects the visual display of the control, call the <xref:System.Windows.Forms.Control.Invalidate%2A> method (that your control inherits from <xref:System.Windows.Forms.Control>) from the `set` accessor.</span></span> <span data-ttu-id="db6c1-109"><xref:System.Windows.Forms.Control.Invalidate%2A>à son tour appelle la <xref:System.Windows.Forms.Control.OnPaint%2A> (méthode), qui redessine le contrôle.</span><span class="sxs-lookup"><span data-stu-id="db6c1-109"><xref:System.Windows.Forms.Control.Invalidate%2A> in turn calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which redraws the control.</span></span> <span data-ttu-id="db6c1-110">Appels multiples à <xref:System.Windows.Forms.Control.Invalidate%2A> entraînant un appel unique à <xref:System.Windows.Forms.Control.OnPaint%2A> pour plus d’efficacité.</span><span class="sxs-lookup"><span data-stu-id="db6c1-110">Multiple calls to <xref:System.Windows.Forms.Control.Invalidate%2A> result in a single call to <xref:System.Windows.Forms.Control.OnPaint%2A> for efficiency.</span></span>  
  
-   <span data-ttu-id="db6c1-111">La bibliothèque de classes .NET Framework fournit des convertisseurs de type pour les types de données courants : entiers, nombres décimaux, valeurs booléennes, etc.</span><span class="sxs-lookup"><span data-stu-id="db6c1-111">The .NET Framework class library provides type converters for common data types such as integers, decimal numbers, Boolean values, and others.</span></span> <span data-ttu-id="db6c1-112">L’objectif d’un convertisseur de type consiste généralement à fournir une conversion de chaînes en valeurs (des données de chaîne vers d’autres types de données).</span><span class="sxs-lookup"><span data-stu-id="db6c1-112">The purpose of a type converter is generally to provide string-to-value conversion (from string data to other data types).</span></span> <span data-ttu-id="db6c1-113">Les types de données courants sont associés à des convertisseurs de type par défaut qui convertissent les valeurs en chaînes et les chaînes vers les types de données adéquats.</span><span class="sxs-lookup"><span data-stu-id="db6c1-113">Common data types are associated with default type converters that convert values into strings and strings into the appropriate data types.</span></span> <span data-ttu-id="db6c1-114">Si vous définissez une propriété d’un type de donnée personnalisé (autrement dit, non standard), il vous faudra appliquer un attribut qui spécifie le convertisseur de type à associer à cette propriété.</span><span class="sxs-lookup"><span data-stu-id="db6c1-114">If you define a property that is a custom (that is, nonstandard) data type, you will have to apply an attribute that specifies the type converter to associate with that property.</span></span> <span data-ttu-id="db6c1-115">Vous pouvez également utiliser un attribut pour associer un éditeur de type avec interface utilisateur personnalisé à une propriété.</span><span class="sxs-lookup"><span data-stu-id="db6c1-115">You can also use an attribute to associate a custom UI type editor with a property.</span></span> <span data-ttu-id="db6c1-116">Un éditeur de type avec interface utilisateur fournit une interface utilisateur permettant de modifier un type de données ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="db6c1-116">A UI type editor provides a user interface for editing a property or data type.</span></span> <span data-ttu-id="db6c1-117">Par exemple, un sélecteur de couleurs est un éditeur de type avec interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="db6c1-117">A color picker is an example of a UI type editor.</span></span> <span data-ttu-id="db6c1-118">Des exemples d’attributs sont donnés à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="db6c1-118">Examples of attributes are given at the end of this topic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db6c1-119">S’il n’y a pas de convertisseur de type ou d’éditeur de type avec interface utilisateur disponible pour votre propriété personnalisée, vous pouvez en implémenter un en suivant les instructions de la page [Étendre la prise en charge au moment du design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span><span class="sxs-lookup"><span data-stu-id="db6c1-119">If a type converter or a UI type editor is not available for your custom property, you can implement one as described in [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).</span></span>  
  
 <span data-ttu-id="db6c1-120">Le fragment de code suivant montre définit une propriété personnalisée nommée `EndColor` pour le contrôle personnalisé `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="db6c1-120">The following code fragment defines a custom property named `EndColor` for the custom control `FlashTrackBar`.</span></span>  
  
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
  
 <span data-ttu-id="db6c1-121">Le fragment de code suivant associe un convertisseur de type et un éditeur de type avec interface utilisateur à la propriété `Value`.</span><span class="sxs-lookup"><span data-stu-id="db6c1-121">The following code fragment associates a type converter and a UI type editor with the property `Value`.</span></span> <span data-ttu-id="db6c1-122">Dans ce cas `Value` est un entier et possède un convertisseur de type par défaut, mais la <xref:System.ComponentModel.TypeConverterAttribute> attribut s’applique à un convertisseur de type personnalisé (`FlashTrackBarValueConverter`) qui permet au concepteur pour l’afficher sous forme de pourcentage.</span><span class="sxs-lookup"><span data-stu-id="db6c1-122">In this case `Value` is an integer and has a default type converter, but the <xref:System.ComponentModel.TypeConverterAttribute> attribute applies a custom type converter (`FlashTrackBarValueConverter`) that enables the designer to display it as a percentage.</span></span> <span data-ttu-id="db6c1-123">L’éditeur de type avec interface utilisateur, `FlashTrackBarValueEditor`, permet d’afficher visuellement le pourcentage.</span><span class="sxs-lookup"><span data-stu-id="db6c1-123">The UI type editor, `FlashTrackBarValueEditor`, allows the percentage to be displayed visually.</span></span> <span data-ttu-id="db6c1-124">Cet exemple montre également que le convertisseur de type ou l’éditeur spécifié par le <xref:System.ComponentModel.TypeConverterAttribute> ou <xref:System.ComponentModel.EditorAttribute> attribut remplace le convertisseur par défaut.</span><span class="sxs-lookup"><span data-stu-id="db6c1-124">This example also shows that the type converter or editor specified by the <xref:System.ComponentModel.TypeConverterAttribute> or <xref:System.ComponentModel.EditorAttribute> attribute overrides the default converter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db6c1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db6c1-125">See Also</span></span>  
 [<span data-ttu-id="db6c1-126">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db6c1-126">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="db6c1-127">Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset</span><span class="sxs-lookup"><span data-stu-id="db6c1-127">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [<span data-ttu-id="db6c1-128">Événements de modification de propriété</span><span class="sxs-lookup"><span data-stu-id="db6c1-128">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [<span data-ttu-id="db6c1-129">Attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db6c1-129">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
