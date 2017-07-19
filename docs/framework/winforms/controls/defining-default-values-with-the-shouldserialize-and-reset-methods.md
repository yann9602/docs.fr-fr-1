---
title: "D&#233;finition de valeurs par d&#233;faut avec les m&#233;thodes ShouldSerialize et Reset | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), méthodes de propriétés"
  - "Reset (méthode)"
  - "ShouldPersist (méthode)"
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# D&#233;finition de valeurs par d&#233;faut avec les m&#233;thodes ShouldSerialize et Reset
`ShouldSerialize` et `Reset` sont des méthodes facultatives que vous pouvez fournir pour une propriété, si cette dernière ne possède pas de valeur par défaut simple.  Si la propriété possède une valeur par défaut simple, vous devez appliquer <xref:System.ComponentModel.DefaultValueAttribute> et fournir plutôt la valeur par défaut au constructeur de classe d'attributs.  Ces deux mécanismes activent les fonctionnalités suivantes dans le concepteur :  
  
-   La propriété indique visuellement, dans l'Explorateur de propriétés, si sa valeur par défaut a été modifiée.  
  
-   L'utilisateur peut cliquer avec le bouton droit sur la propriété et choisir **Reset** pour restaurer sa valeur par défaut.  
  
-   Le concepteur génère un code plus efficace.  
  
    > [!NOTE]
    >  Appliquez le <xref:System.ComponentModel.DefaultValueAttribute> ou fournissez les méthodes `Reset`*NomPropriété* et `ShouldSerialize`*NomPropriété*.  N'utilisez pas les deux procédures.  
  
 La méthode `Reset`*NomPropriété* affecte à une propriété sa valeur par défaut, comme illustré dans le fragment de code suivant.  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  Si une propriété ne dispose pas de méthode `Reset`, si elle n'est pas marquée avec <xref:System.ComponentModel.DefaultValueAttribute> et si elle ne possède pas de valeur par défaut fournie dans sa déclaration, l'option `Reset` est désactivée pour cette propriété dans le menu contextuel de la fenêtre **Propriétés** du concepteur Windows Forms de [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Les concepteurs tels que [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] utilisent la méthode `ShouldSerialize`*NomPropriété* pour vérifier si une propriété ne possède plus sa valeur par défaut et écrivent du code dans le formulaire uniquement si une propriété a été modifiée, ce qui permet une génération de code plus efficace.  Par exemple :  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 Vous trouverez ci\-dessous un exemple de code complet.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 Dans ce cas, même lorsque la valeur de la variable privée accédée par la propriété `MyFont` est `null`, l'explorateur de propriétés n'affiche pas `null` ; à la place, il affiche la propriété <xref:System.Windows.Forms.Control.Font%2A> du parent, si elle n'est pas `null`, ou la valeur <xref:System.Windows.Forms.Control.Font%2A> par défaut définie dans <xref:System.Windows.Forms.Control>.  Par conséquent, la valeur par défaut de `MyFont`  ne peut pas être simplement définie et aucun <xref:System.ComponentModel.DefaultValueAttribute> ne peut être appliqué à cette propriété.  À la place, les méthodes `ShouldSerialize` et `Reset` doivent être implémentées pour la propriété `MyFont`.  
  
## Voir aussi  
 [Propriétés dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [Définition d'une propriété](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)   
 [Événements de modification de propriété](../../../../docs/framework/winforms/controls/property-changed-events.md)