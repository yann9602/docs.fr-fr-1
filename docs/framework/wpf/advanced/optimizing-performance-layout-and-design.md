---
title: "Optimisation des performances&#160;: disposition et conception | Microsoft Docs"
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
  - "considérations de design"
  - "passe de disposition"
  - "disposition, optimiser les performances"
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Optimisation des performances&#160;: disposition et conception
La conception de votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut affecter ses performances en créant des charges mémoire inutiles pour calculer la disposition et valider des références d'objet.  La construction d'objets, en particulier au moment de l'exécution, peut affecter les caractéristiques de performance de votre application.  
  
 Cette rubrique fournit des recommandations de performance dans ces domaines.  
  
## Disposition  
 Le terme « passe de disposition » décrit le processus de mesure et réorganisation des membres d'un <xref:System.Windows.Controls.Panel>, la collection d'enfants de l'objet dérivé, et les dessine ensuite l'écran.  Le passe de disposition est un processus mathématique intensif \(plus le nombre d'enfants est élevé dans la collection, plus le nombre de calculs requis est grand\).  Par exemple, à chaque fois qu'un objet <xref:System.Windows.UIElement> enfant dans la collection modifie sa position, il a la possibilité de déclencher une nouvelle passe par le système de disposition.  Étant donné que la relation entre les caractéristiques d'objet et le comportement de disposition est étroite, il est important de comprendre le type des événements qui peuvent appeler le système de disposition.  Votre application sera plus performante si vous réduisez autant que possible tous les appels inutiles de la passe de disposition.  
  
 Le système de disposition effectue deux passes pour chaque membre enfant d'une collection , une passe de mesure et une passe de réorganisation.  Chaque objet enfant dispose de sa propre implémentation substituée des méthodes <xref:System.Windows.UIElement.Measure%2A> et <xref:System.Windows.UIElement.Arrange%2A> pour fournir son propre comportement de disposition spécifique.  Dans sa forme la plus simple, la disposition est un système récursif qui conduit au dimensionnement, positionnement et dessin d'un élément à l'écran.  
  
-   Un objet <xref:System.Windows.UIElement> enfant commence le processus de disposition en ayant en premier ses propriétés principales mesurées.  
  
-   Les propriétés <xref:System.Windows.FrameworkElement> de l'objet liées à la taille, telles que <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>et <xref:System.Windows.FrameworkElement.Margin%2A>, sont évaluées.  
  
-   La logique spécifique à <xref:System.Windows.Controls.Panel> est appliquée, telle que la propriété <xref:System.Windows.Controls.DockPanel.Dock%2A> du <xref:System.Windows.Controls.DockPanel>, ou la propriété <xref:System.Windows.Controls.StackPanel.Orientation%2A> du <xref:System.Windows.Controls.StackPanel>.  
  
-   Le contenu est réorganisé, ou  positionné, après que tous les objets enfants ont été mesurés.  
  
-   La collection d'objets enfants est dessinée à l'écran.  
  
 Le processus de la passe de disposition est encore appelé si l'une des actions suivantes se produit :  
  
-   Un objet enfant est ajouté à la collection.  
  
-   Un <xref:System.Windows.FrameworkElement.LayoutTransform%2A> est appliqué à l'objet enfant.  
  
-   La méthode <xref:System.Windows.UIElement.UpdateLayout%2A> est appelée pour l'objet enfant.  
  
-   Lorsqu'une modification est apportée à la valeur d'une [propriété de dépendance](GTMT) qui est marquée avec les métadonnées affectant les passes de mesure ou de réorganisation.  
  
### Utiliser le panneau le plus efficace si possible  
 La complexité du processus de disposition est directement basé sur le comportement de disposition du <xref:System.Windows.Controls.Panel>\- éléments dérivés que vous utilisez.  Par exemple, un contrôle <xref:System.Windows.Controls.Grid> ou <xref:System.Windows.Controls.StackPanel> fournit beaucoup plus de fonctionnalités qu'un contrôle <xref:System.Windows.Controls.Canvas>.  Le prix de ces fonctionnalités supérieures est une augmentation des coûts de performance.  Toutefois, si vous n'avez pas besoin des fonctionnalités qu'un contrôle <xref:System.Windows.Controls.Grid> fournit, vous devez utiliser les alternatives moins chères, telles qu'un <xref:System.Windows.Controls.Canvas> ou un panneau personnalisé.  
  
 Pour plus d'informations, consultez [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
### Mettre à jour plutôt que remplacer un RenderTransform  
 Vous êtes peut\-être en mesure de mettre à jour un <xref:System.Windows.Media.Transform> plutôt que de le remplacer comme valeur d'une propriété <xref:System.Windows.UIElement.RenderTransform%2A>.  C'est notamment le cas dans des scénarios qui impliquent une animation.  En mettant à jour un <xref:System.Windows.Media.Transform>existant, vous évitez d'initialiser un calcul de disposition inutile.  
  
### Générer votre arborescence Haut\-Bas  
 Lorsqu'un nœud est ajouté ou supprimé de l'[arborescence logique](GTMT), les invalidations de propriété sont déclenchées sur le parent du nœud et tous ses enfants.  En conséquence, un modèle de construction de haut en bas doit toujours être suivi pour éviter le coût d'invalidations inutiles sur les nœuds qui ont déjà été validés.  La table suivante affiche la différence de vitesse d'exécution entre la génération d'une arborescence haut\-bas et bas\-haut, dans laquelle l'arborescence comprend 150 niveaux avec un <xref:System.Windows.Controls.TextBlock> et un <xref:System.Windows.Controls.DockPanel> à chaque niveau.  
  
|**Action**|**Construction d'arborescence \(en ms\)**|**Rendu, y compris la construction d'arborescence \(en ms\)**|  
|----------------|-----------------------------------------------|-------------------------------------------------------------------|  
|Ascendante|366|454|  
|Haut\-bas|11|96|  
  
 L'exemple de code suivant illustre la création d'une arborescence de haut en bas.  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Pour plus d'informations sur l'arborescence logique, consultez [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
## Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Comportement d'objets](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)   
 [Disposition](../../../../docs/framework/wpf/advanced/layout.md)