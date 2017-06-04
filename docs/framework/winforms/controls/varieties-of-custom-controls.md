---
title: "Vari&#233;t&#233;s de contr&#244;les personnalis&#233;s | Microsoft Docs"
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
  - "contrôles composites"
  - "contrôles (Windows Forms), composites"
  - "contrôles (Windows Forms), étendues"
  - "contrôles (Windows Forms), types de"
  - "contrôles (Windows Forms), contrôles utilisateur"
  - "contrôles personnalisés (Windows Forms)"
  - "contrôles étendus"
  - "contrôles utilisateur (Windows Forms)"
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Vari&#233;t&#233;s de contr&#244;les personnalis&#233;s
Avec le .NET Framework, vous pouvez développer et implémenter de nouveaux contrôles.  Vous pouvez étendre les fonctionnalités du contrôle utilisateur familier mais aussi de contrôles existants via l'héritage.  Vous pouvez également écrire des contrôles personnalisés qui exécutent leur propre peinture.  
  
 Vous aurez parfois du mal à choisir entre ces différents types de contrôle.  Cette rubrique met en lumière les différences entre les divers types de contrôle que vous pouvez hériter et fournit des informations qui vous permettent de choisir un type particulier de contrôle pour votre projet.  
  
> [!NOTE]
>  Pour plus d'informations sur la création d'un contrôle à utiliser sur les Web Forms, consultez [Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md).  
  
## Classe de base Control  
 La classe <xref:System.Windows.Forms.Control> est la classe de base pour les contrôles Windows Forms.  Elle fournit l'infrastructure requise pour la visualisation dans les applications Windows Forms.  
  
 La classe <xref:System.Windows.Forms.Control> effectue les tâches suivantes pour fournir la visualisation dans les applications Windows Forms :  
  
-   expose un handle de fenêtre ;  
  
-   gère l'acheminement de messages ;  
  
-   fournit des événements souris de clavier, ainsi que beaucoup d'autres événements d'interface utilisateur ;  
  
-   fournit des fonctionnalités de disposition avancées ;  
  
-   Contient beaucoup de propriétés spécifiques à l'affichage visuel, comme <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A> et <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Fournit la sécurité et la prise en charge du threading nécessaires pour qu'un contrôle Windows Forms puisse agir comme un contrôle Microsoft® ActiveX®.  
  
 Comme une grande partie de l'infrastructure est fournie par la classe de base, il est relativement aisé de développer vos propres contrôles Windows Forms.  
  
## Types de contrôle  
 Windows Forms prend en charge trois types de contrôle définis par l'utilisateur : *composite*, *étendu* et *personnalisé*.  Les sections suivantes décrivent chaque type de contrôle et donnent des recommandations pour choisir le type à utiliser dans vos projets.  
  
### Contrôles composites  
 Un contrôle composite est une collection de contrôles Windows Forms encapsulés dans un même conteneur.  Ce type de contrôle est parfois appelé un *contrôle utilisateur*.  Les contrôles contenus sont appelés des *contrôles constitutifs*.  
  
 Un contrôleur composite contient toutes les fonctionnalités inhérentes à chacun des contrôles Windows Forms contenus et vous permet d'exposer et de lier sélectivement leurs propriétés.  Un contrôle composite fournit également un grand nombre de fonctionnalités de manipulation de clavier par défaut, sans aucun effort de développement supplémentaire de votre part.  
  
 Par exemple, un contrôle composite pourrait être construit pour afficher les données d'adresses personnalisées d'une base de données.  Ce contrôle pourrait inclure un contrôle <xref:System.Windows.Forms.DataGridView> pour afficher les champs de base de données, un <xref:System.Windows.Forms.BindingSource> pour gérer la création d'une liaison avec une source de données et un contrôle <xref:System.Windows.Forms.BindingNavigator> pour parcourir les enregistrements.  Vous pourriez exposer des propriétés de liaison de données sélectivement, et emballer et réutiliser le contrôle entier d'application à l'application.  Pour obtenir un exemple de ce type de contrôle composite, consultez [Comment : appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Pour créer un contrôle composite, dérivez de la classe <xref:System.Windows.Forms.UserControl>.  La classe de base <xref:System.Windows.Forms.UserControl> fournit le routage clavier pour les contrôles enfants et permet à ces derniers de fonctionner en tant que groupe.  Pour plus d'informations, consultez [Développement d'un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
 **Recommandation**  
  
 Optez pour l'héritage de la classe <xref:System.Windows.Forms.UserControl> si :  
  
-   vous voulez combiner les fonctionnalités de plusieurs contrôles Windows Forms dans une même entité réutilisable.  
  
### Contrôles étendus  
 Vous pouvez créer un contrôle hérité à partir de n'importe quel contrôle Windows Forms existant.  Cette approche vous permet de conserver toutes les fonctionnalités inhérentes au contrôle Windows Forms et même de les enrichir en y ajoutant des propriétés, des méthodes personnalisées ou encore d'autres fonctionnalités.  Avec cette option, vous pouvez substituer la logique de peinture du contrôle de base, puis étendre son interface utilisateur en modifiant son apparence.  
  
 Par exemple, vous pouvez créer un contrôle dérivé du contrôle <xref:System.Windows.Forms.Button> qui suit le nombre de fois qu'un utilisateur a cliqué dessus.  
  
 Dans certains cas, vous pouvez également ajouter une apparence personnalisée à l'interface utilisateur graphique de votre contrôle en substituant la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base.  Pour un bouton étendu qui suit les clics, vous pouvez substituer la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> pour appeler l'implémentation de base de <xref:System.Windows.Forms.Control.OnPaint%2A>, puis dessiner le nombre de clics dans un angle de la zone cliente du contrôle <xref:System.Windows.Forms.Button>.  
  
 **Recommandation**  
  
 Optez pour l'héritage d'un contrôle Windows Forms si :  
  
-   les fonctionnalités dont vous avez besoin sont pour la plupart identiques à celles d'un contrôle Windows Forms existant ;  
  
-   vous n'avez pas besoin d'une interface utilisateur graphique personnalisée ou vous souhaitez en créer une nouvelle pour un contrôle existant.  
  
### Contrôles personnalisés  
 Une autre méthode consiste à créer un contrôle presque entièrement nouveau en héritant de la classe <xref:System.Windows.Forms.Control>.  La classe <xref:System.Windows.Forms.Control> fournit toutes les fonctionnalités élémentaires requises par les contrôles, notamment les événements de gestion de souris et de clavier, mais pas de fonctionnalité spécifique ni d'interface graphique.  
  
 Créer un contrôle par héritage de la classe <xref:System.Windows.Forms.Control> exige beaucoup plus de réflexion et d'efforts que d'hériter d'un <xref:System.Windows.Forms.UserControl> ou d'un contrôle Windows Forms existant.  Dans la mesure où une bonne partie de l'implémentation vous est confiée, votre contrôle peut avoir une souplesse supérieure à celle d'un contrôle composite ou étendu, et vous pouvez faire en sorte que votre contrôle soit exactement adapté à vos besoins.  
  
 Pour implémenter un contrôle personnalisé, vous devez écrire le code pour l'événement <xref:System.Windows.Forms.Control.OnPaint%2A> du contrôle, ainsi que tout code spécifique à une fonctionnalité dont vous avez besoin.  Vous pouvez également substituer directement la méthode <xref:System.Windows.Forms.Control.WndProc%2A> et gérer directement les messages des fenêtres.  C'est la façon la plus puissante de créer un contrôle, mais pour utiliser cette technique efficacement, vous devez être familiarisé avec l'API Win32® de Microsoft.  
  
 Un contrôle d'horloge imitant l'apparence et le comportement d'une horloge analogique est un exemple de contrôle personnalisé.  En effet, il est fait appel à la peinture personnalisée pour simuler le déplacement des aiguilles sur le cadran en réponse aux événements <xref:System.Windows.Forms.Timer.Tick> d'un composant <xref:System.Windows.Forms.Timer> interne.  Pour plus d'informations, consultez [Comment : développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 **Recommandation**  
  
 Optez pour l'héritage de la classe <xref:System.Windows.Forms.Control> si :  
  
-   vous voulez fournir une représentation graphique personnalisée de votre contrôle ;  
  
-   vous devez implémenter des fonctionnalités personnalisées que n'offrent pas les contrôles standard.  
  
### Contrôles ActiveX  
 Bien que l'infrastructure Windows Forms ait été optimisée pour l'hébergement de contrôles Windows Forms, il est toujours possible d'y inclure des contrôles ActiveX.  Il existe une prise en charge pour cette tâche dans Visual Studio.  Pour plus d'informations, consultez [Comment : ajouter des contrôles ActiveX aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).  
  
### Contrôles sans fenêtre  
 Les technologies Visual Basic® 6.0 et ActiveX de Microsoft prennent en charge des contrôles *sans fenêtre*.  Les contrôles sans fenêtre ne sont pas pris en charge dans Windows Forms.  
  
## Expérience de design personnalisé  
 Si vous devez implémenter une expérience au moment du design personnalisée, vous pouvez créer votre propre concepteur.  Pour les contrôles composites, dérivez votre classe de concepteur personnalisée des classes <xref:System.Windows.Forms.Design.ParentControlDesigner> ou <xref:System.Windows.Forms.Design.DocumentDesigner>.  Pour les contrôles étendus et personnalisés, dérivez votre classe de concepteur personnalisée de la classe <xref:System.Windows.Forms.Design.ControlDesigner>.  
  
 Utilisez le <xref:System.ComponentModel.DesignerAttribute> pour associer votre contrôle à votre concepteur.  Pour plus d'informations, consultez [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md) et [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md).  
  
## Voir aussi  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Comment : développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)   
 [Développement d'un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)   
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [How to: Create a Windows Forms Control That Takes Advantage of Design\-Time Features](../Topic/How%20to:%20Create%20a%20Windows%20Forms%20Control%20That%20Takes%20Advantage%20of%20Design-Time%20Features.md)