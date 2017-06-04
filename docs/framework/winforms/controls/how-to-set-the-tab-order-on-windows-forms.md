---
title: "Comment&#160;: d&#233;finir l&#39;ordre de tabulation dans les Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TabStop"
  - "TabIndex"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), définir l'ordre de tabulation"
  - "ordre de tabulation, contrôles sur des Windows Forms"
  - "contrôles Windows Forms, définir l'ordre de tabulation"
  - "Windows Forms, définir l'ordre de tabulation"
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: d&#233;finir l&#39;ordre de tabulation dans les Windows Forms
L'ordre de tabulation est l'ordre dans lequel un utilisateur déplace le focus d'un contrôle à l'autre en appuyant sur la touche TABULATION.  Chaque formulaire possède son propre ordre de tabulation.  Par défaut, l'ordre de tabulation suit celui dans lequel les contrôles ont été créés.  La numérotation de l'ordre de tabulation débute à zéro.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir l'ordre de tabulation d'un contrôle  
  
1.  Dans le menu **Affichage**, cliquez sur **Ordre de tabulation**.  
  
     Vous activez ainsi le mode de sélection de l'ordre de tabulation dans le formulaire.  Un numéro \(représentant la propriété <xref:System.Windows.Forms.Control.TabIndex%2A>\) apparaît dans le coin supérieur gauche de chaque contrôle.  
  
2.  Cliquez sur les contrôles l'un après l'autre pour déterminer l'ordre de tabulation souhaité.  
  
    > [!NOTE]
    >  La place d'un contrôle dans l'ordre de tabulation peut être définie à n'importe quelle valeur supérieure ou égale à 0.  Lorsque les doublons se produisent, l'ordre de plan des deux contrôles est évalué et le contrôle supérieur est tabulé vers le premier.  \(L'ordre de plan détermine la superposition visuelle des contrôles d'un formulaire sur l'axe z \[profondeur\].  Il détermine les contrôles qui sont placés en avant\-plan des autres.\). Pour plus d'informations sur l'ordre de plan, consultez [Superposition d'objets dans les Windows Forms](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
3.  Lorsque vous avez terminé, cliquez sur **Ordre de tabulation** dans le menu **Affichage** pour quitter le mode de l'ordre de tabulation.  
  
    > [!NOTE]
    >  Les contrôles qui ne peuvent recevoir le focus, ainsi que les contrôles désactivés et invisibles, ne possèdent pas de propriété <xref:System.Windows.Forms.Control.TabIndex%2A> et ne sont pas inclus dans l'ordre de tabulation.  Lorsque l'utilisateur appuie sur la touche TABULATION, ces contrôles sont ignorés.  
  
 L'ordre de tabulation peut également être défini dans la fenêtre Propriétés à l'aide de la propriété <xref:System.Windows.Forms.Control.TabIndex%2A>.  La propriété <xref:System.Windows.Forms.Control.TabIndex%2A> d'un contrôle détermine son rang dans l'ordre de tabulation.  Par défaut, le premier contrôle prend une valeur <xref:System.Windows.Forms.Control.TabIndex%2A> de 0, le deuxième de 1, et ainsi de suite.  
  
 En outre, par défaut, un contrôle <xref:System.Windows.Forms.GroupBox> possède sa propre valeur <xref:System.Windows.Forms.Control.TabIndex%2A> qui est un nombre entier.  Un contrôle <xref:System.Windows.Forms.GroupBox> ne peut recevoir le focus au moment de l'exécution.  Ainsi, chaque contrôle dans un <xref:System.Windows.Forms.GroupBox> a sa propre valeur <xref:System.Windows.Forms.Control.TabIndex%2A> décimale, en commençant par .0.  Naturellement, comme le <xref:System.Windows.Forms.Control.TabIndex%2A> d'un contrôle <xref:System.Windows.Forms.GroupBox> est incrémenté, les contrôles qu'il contient seront incrémentés en conséquence.  Ainsi, si vous remplacez une valeur <xref:System.Windows.Forms.Control.TabIndex%2A> de 5 par 6, la valeur <xref:System.Windows.Forms.Control.TabIndex%2A> du premier contrôle de son groupe devient automatiquement 6.0, et ainsi de suite.  
  
 Enfin, il est possible de soustraire de l'ordre de tabulation n'importe quel contrôle d'un formulaire.  En général, le fait d'appuyer plusieurs fois de suite sur la touche TABULATION au moment de l'exécution a pour effet de sélectionner les contrôles dans l'ordre de tabulation.  En désactivant la propriété <xref:System.Windows.Forms.Control.TabStop%2A>, vous pouvez faire en sorte qu'un contrôle ne soit pas pris en compte dans l'ordre de tabulation d'un formulaire.  
  
#### Pour supprimer un contrôle de l'ordre de tabulation  
  
1.  Dans la fenêtre Propriétés, affectez à la propriété <xref:System.Windows.Forms.Control.TabStop%2A> du contrôle la valeur `false`.  
  
     Un contrôle dont la propriété <xref:System.Windows.Forms.Control.TabStop%2A> a la valeur `false` conserve son rang dans l'ordre de tabulation, bien qu'il ne soit pas pris en compte lorsque vous passez successivement d'un contrôle à l'autre à l'aide de la touche TABULATION.  
  
    > [!NOTE]
    >  Au moment de l'exécution, un groupe de cases d'option ne correspond qu'à un seul arrêt de tabulation.  Le bouton sélectionné \(autrement dit, celui dont la propriété <xref:System.Windows.Forms.RadioButton.Checked%2A> a la valeur `true`\) voit sa propriété <xref:System.Windows.Forms.Control.TabStop%2A> prendre automatiquement la valeur `true`, alors que les autres boutons voient leur propriété <xref:System.Windows.Forms.Control.TabStop%2A> prendre la valeur `false`.  Pour plus d'informations sur le regroupement des contrôles <xref:System.Windows.Forms.RadioButton>, consultez [Groupement de contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)