---
title: "Variétés de contrôles personnalisés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7cd45c85f155da975ca17961ca49a5dc89800a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="varieties-of-custom-controls"></a>Variétés de contrôles personnalisés
.NET Framework vous offre la possibilité de développer et d’implémenter de nouveaux contrôles. Vous pouvez étendre les fonctionnalités du contrôle utilisateur standard et des contrôles existants grâce à l’héritage. Vous pouvez également créer des contrôles personnalisés qui gèrent eux-même leur apparence.  
  
 Le choix du type de contrôle à créer peut être délicat. Cette rubrique met en évidence les différences entre les nombreux types de contrôles à partir desquels vous pouvez hériter et vous guide dans le choix du type de contrôle adapté à votre projet.  
  
> [!NOTE]
>  Pour plus d’informations sur la création d’un contrôle pour des Web Forms, consultez l’article [Développement de contrôles serveur ASP.NET personnalisés](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="base-control-class"></a>Classe de contrôle de base  
 Le <xref:System.Windows.Forms.Control> est la classe de base pour les contrôles Windows Forms. Elle fournit l’infrastructure requise pour l’affichage dans les applications Windows Forms.  
  
 La <xref:System.Windows.Forms.Control> classe effectue les tâches suivantes pour fournir la visualisation dans les applications Windows Forms :  
  
-   Elle expose un handle de fenêtre.  
  
-   Elle gère le routage des messages.  
  
-   Elle fournit des événements de clavier et de souris, ainsi que de nombreux autres événements d’interface utilisateur.  
  
-   Elle fournit des fonctionnalités de disposition avancées.  
  
-   Contient de nombreuses propriétés spécifiques à l’affichage visuel, tel que <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, et <xref:System.Windows.Forms.Control.Width%2A>.  
  
-   Elle fournit la sécurité et la prise en charge des threads dont un contrôle Windows Forms a besoin pour se comporter comme un contrôle Microsoft® ActiveX®.  
  
 Étant donné que la majeure partie de l’infrastructure est fournie par la classe de base, il est relativement facile de développer vos propres contrôles Windows Forms.  
  
## <a name="kinds-of-controls"></a>Types de contrôles  
 Windows Forms prend en charge trois types de contrôles définis par l’utilisateur : *composite*, *étendu* et *personnalisé*. Les sections suivantes décrivent chaque type de contrôle et fournissent des recommandations pour choisir le type de contrôle à utiliser dans vos projets.  
  
### <a name="composite-controls"></a>Contrôles composites  
 Un contrôle composite est un ensemble de contrôles Windows Forms encapsulés dans un conteneur commun. Ce type de contrôle est parfois appelé *contrôle utilisateur*. Les contrôles contenus sont appelés *contrôles constitutifs*.  
  
 Un contrôle composite contient toutes les fonctionnalités inhérentes associées à chacun des contrôles Windows Forms contenus et vous permet d’exposer et de lier leurs propriétés de manière sélective. Un contrôle composite fournit également un grand nombre de fonctionnalités de gestion du clavier par défaut sans aucun effort de développement supplémentaire de votre part.  
  
 Un contrôle composite peut par exemple être conçu pour afficher des données d’adresses de clients à partir d’une base de données. Ce contrôle peut inclure un <xref:System.Windows.Forms.DataGridView> contrôle pour afficher les champs de la base de données, un <xref:System.Windows.Forms.BindingSource> pour gérer la liaison à une source de données et un <xref:System.Windows.Forms.BindingNavigator> pour parcourir les enregistrements de contrôle. Vous pourriez exposer de manière sélective les propriétés de liaison de données, mais aussi empaqueter et réutiliser l’ensemble du contrôle d’une application à l’autre. Pour obtenir un exemple de ce type de contrôle composite, consultez l’article [Comment : appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Pour créer un contrôle composite, dérivez de la <xref:System.Windows.Forms.UserControl> classe. La <xref:System.Windows.Forms.UserControl> classe de base fournit le routage clavier pour les contrôles enfants et permet des contrôles enfants fonctionner en tant que groupe. Pour plus d’informations, consultez l’article [Développement d’un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
 **Recommendation**  
  
 Héritez de la classe <xref:System.Windows.Forms.UserControl> si :  
  
-   vous souhaitez combiner les fonctionnalités de plusieurs contrôles Windows Forms dans une même entité réutilisable.  
  
### <a name="extended-controls"></a>Contrôles étendus  
 Vous pouvez dériver un contrôle hérité à partir de n'importe quel contrôle Windows Forms existant. Cette approche vous permet de conserver toutes les fonctionnalités inhérentes d’un contrôle Windows Forms et de les étendre en y ajoutant des propriétés et des méthodes personnalisées ou d’autres fonctionnalités. Avec cette option, vous pouvez remplacer la logique de peinture du contrôle de base, puis étendre son interface utilisateur en modifiant son apparence.  
  
 Par exemple, vous pouvez créer un contrôle dérivé de la <xref:System.Windows.Forms.Button> contrôle qui effectue le suivi du nombre de fois où un utilisateur a cliqué dessus.  
  
 Dans certains cas, vous pouvez également ajouter une apparence personnalisée à l’interface utilisateur graphique de votre contrôle en substituant la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode de la classe de base. Pour un bouton étendu qui suit les clics, vous pouvez remplacer le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode à appeler l’implémentation de base de <xref:System.Windows.Forms.Control.OnPaint%2A>, puis dessinez le nombre de clics dans un angle de la <xref:System.Windows.Forms.Button> zone cliente du contrôle.  
  
 **Recommendation**  
  
 Héritez d'un contrôle Windows Forms si :  
  
-   la plupart des fonctionnalités dont vous avez besoin sont déjà identiques à un contrôle Windows Forms existant ;  
  
-   vous n’avez pas besoin d’une interface utilisateur graphique personnalisée ou vous souhaitez concevoir une nouvelle interface utilisateur graphique pour un contrôle existant.  
  
### <a name="custom-controls"></a>Contrôles personnalisés  
 Une autre façon de créer un contrôle consiste à créer un tout début en héritant de <xref:System.Windows.Forms.Control>. La <xref:System.Windows.Forms.Control> classe fournit toutes les fonctionnalités de base requises par les contrôles, y compris la souris et clavier de la gestion des événements, mais aucune fonctionnalité spécifique ou l’interface graphique.  
  
 Création d’un contrôle en héritant de la <xref:System.Windows.Forms.Control> classe nécessite beaucoup plus de réflexion et d’efforts que d’hériter de <xref:System.Windows.Forms.UserControl> ou d’un contrôle Windows Forms existant. Comme vous gérez une grande partie de l’implémentation, votre contrôle peut avoir une plus grande flexibilité qu’un contrôle composite ou étendu, et vous pouvez personnaliser votre contrôle pour l’adapter à vos besoins spécifiques.  
  
 Pour implémenter un contrôle personnalisé, vous devez écrire du code pour le <xref:System.Windows.Forms.Control.OnPaint%2A> l’événement de contrôle, ainsi que tout code spécifique à la fonctionnalité que vous avez besoin. Vous pouvez également remplacer le <xref:System.Windows.Forms.Control.WndProc%2A> (méthode) et le handle windows directement les messages. Il s’agit de la façon la plus efficace pour créer un contrôle, à condition de bien connaître l’API Microsoft Win32®.  
  
 Un contrôle personnalisé peut par exemple être un contrôle d’horloge imitant l’apparence et le comportement d’une horloge analogique. Peinture personnalisée est appelée pour déclencher les aiguilles de l’horloge pour déplacer en réponse à <xref:System.Windows.Forms.Timer.Tick> événements à partir d’une commande interne <xref:System.Windows.Forms.Timer> composant. Pour plus d’informations, consultez l’article [Comment : développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 **Recommendation**  
  
 Héritez de la classe <xref:System.Windows.Forms.Control> si :  
  
-   vous souhaitez fournir une représentation graphique personnalisée de votre contrôle ;  
  
-   vous devez implémenter des fonctionnalités personnalisées qui ne sont pas disponible via les contrôles standard.  
  
### <a name="activex-controls"></a>Contrôles ActiveX  
 Même si l’infrastructure Windows Forms a été optimisée pour héberger des contrôles Windows Forms, vous pouvez tout de même utiliser des contrôles ActiveX. Cette tâche est prise en charge dans Visual Studio. Pour plus d’informations, consultez l’article [Comment : ajouter des contrôles ActiveX aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md).  
  
### <a name="windowless-controls"></a>Contrôles sans fenêtre  
 Les technologies Microsoft Visual Basic® 6.0 et ActiveX prennent en charge les contrôles *sans fenêtre*. Les contrôles sans fenêtre ne sont pas pris en charge dans les Windows Forms.  
  
## <a name="custom-design-experience"></a>Conception personnalisée  
 Si vous devez implémenter une expérience de conception personnalisée, vous pouvez créer votre propre concepteur. Pour les contrôles composites, dérivez votre classe de concepteur personnalisé de la <xref:System.Windows.Forms.Design.ParentControlDesigner> ou <xref:System.Windows.Forms.Design.DocumentDesigner> classes. Pour les contrôles étendus et personnalisés, dérivez votre classe de concepteur personnalisé de la <xref:System.Windows.Forms.Design.ControlDesigner> classe.  
  
 Utilisez le <xref:System.ComponentModel.DesignerAttribute> pour associer votre contrôle à votre concepteur. Pour plus d’informations, consultez les articles [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2) et [Comment : créer un contrôle Windows Forms qui bénéficie des fonctionnalités au moment du design](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Guide pratique pour développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Développement d’un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Comment : créer un contrôle Windows Forms qui bénéficie des fonctionnalités au moment du design](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)
