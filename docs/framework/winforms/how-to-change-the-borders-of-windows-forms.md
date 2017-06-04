---
title: "Comment&#160;: modifier les bordures des Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Forms, modifier les bordures"
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: modifier les bordures des Windows Forms
Vous pouvez choisir parmi plusieurs styles de bordure quand vous déterminez l'apparence et le comportement de vos Windows Forms.  En modifiant la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A>, vous pouvez contrôler le comportement de redimensionnement du formulaire.  De plus, la définition de <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affecte l'affichage de la barre de légende et de ses boutons.  Pour plus d'informations, consultez <xref:System.Windows.Forms.FormBorderStyle>.  
  
 Cette tâche est très bien prise en charge dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 Consultez également [Comment : modifier les bordures des Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/yettzh3e%20\(v=vs.110\)).  
  
### Pour définir le style de bordure des Windows Forms par programmation  
  
-   Affectez à la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A> le style souhaité.  L'exemple de code suivant affecte <xref:System.Windows.Forms.FormBorderStyle> comme style de bordure du formulaire `DlgBx1` .  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     Consultez également [Comment : créer des boîtes de dialogue au moment du design](http://msdn.microsoft.com/library/55cz5x2c%20\(v=vs.110\)).  
  
     En outre, si vous avez choisi pour le formulaire un style de bordure qui fournit des boutons facultatifs **Réduire** et **Agrandir**, vous pouvez spécifier si vous souhaitez que ces boutons fonctionnent.  Ils sont utiles quand vous souhaitez contrôler étroitement l'expérience utilisateur.  Les boutons **Réduire** et **Agrandir** sont activés par défaut et vous pouvez manipuler leur fonctionnalité via la fenêtre **Propriétés**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.FormBorderStyle>   
 <xref:System.Windows.Forms.FormBorderStyle>   
 [Mise en route des Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)