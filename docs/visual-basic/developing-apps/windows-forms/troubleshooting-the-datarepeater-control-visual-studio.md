---
title: "Dépannage des problèmes liés au contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d630dbf8601eeddd5ce3ea02696891a1087f71f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>Dépannage des problèmes liés au contrôle DataRepeater (Visual Studio)
Cette rubrique répertorie les problèmes courants qui peuvent se produire lorsque vous travaillez avec le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>DataRepeater clavier et les événements de souris ne sont pas déclenchés.  
 Certains <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> les événements de contrôle, comme les événements de clavier et souris, ne sont pas déclenchés. Ceci est normal. Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle lui-même est un conteneur pour <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> des objets et ne sont pas accessibles au moment de l’exécution. Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> n’expose pas d’événements au moment du design. Par conséquent, en cliquant sur un élément ou en appuyant sur une touche lorsque l’élément a le focus ne déclenche pas d’événement.  
  
 À cette exception est levée quand le <xref:System.Windows.Forms.Control.Padding%2A> est définie sur une grande valeur suffisante pour exposer les bords de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Dans ce cas, en cliquant dans la marge exposée déclenche les événements de souris.  
  
 Pour résoudre ce problème, ajoutez un <xref:System.Windows.Forms.Panel> le contrôle à la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> section de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôler, puis ajoutez le reste des contrôles à le <xref:System.Windows.Forms.Panel>. Vous pouvez ensuite ajouter le code pour le <xref:System.Windows.Forms.Panel> gestionnaires d’événements pour les événements de clavier et souris.  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>Le contrôle DataRepeater est partiellement masqué derrière le navigateur de liaison  
 Lorsque vous ajoutez un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> le contrôle à un formulaire, puis ajoutez les contrôles liés aux données à partir de la **des Sources de données** fenêtre, le <xref:System.Windows.Forms.BindingNavigator> contrôle peut apparaître au-dessus de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Il s’agit d’une limitation connue de le **des Sources de données** fenêtre et est cohérent avec le comportement d’autres contrôles, tels que le <xref:System.Windows.Forms.DataGridView> contrôle.  
  
 Vous pouvez déplacer le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> inférieure à la <xref:System.Windows.Forms.BindingNavigator> contrôle au moment du design ou ajouter du code qui ressemble à ce qui suit dans le `Load` Gestionnaire d’événements.  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>Les contrôles ne sont pas affichés correctement au moment de l’exécution  
 Certains contrôles dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle ne peut pas être affiché comme prévu au moment de l’exécution. Le processus utilisé pour cloner des contrôles depuis le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> à le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> ne peut pas toujours déterminer toutes les propriétés de tous les contrôles. Par exemple, si vous ajoutez un indépendant <xref:System.Windows.Forms.ListBox> le contrôle à un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle au moment du design et de remplir ses <xref:System.Windows.Forms.ListBox.Items%2A> collection avec une liste de chaînes, la <xref:System.Windows.Forms.ListBox> sera vide au moment de l’exécution. Il s’agit, car le processus de clonage ne peut pas prendre en compte la <xref:System.Windows.Forms.ListBox.Items%2A> propriété.  
  
 Vous pouvez résoudre des problèmes tels que cela en restaurant les propriétés manquantes dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> événement qui se produit après le clonage par défaut est terminé. L’exemple suivant montre comment réparer la <xref:System.Windows.Forms.ListBox.Items%2A> collection d’un <xref:System.Windows.Forms.ListBox> en contrôler le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> Gestionnaire d’événements.  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>Le symbole de sélection de l’en-tête de l’élément est manquant  
 Lorsque vous modifiez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriété de l’en-tête de l’élément dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle, certains choix de couleurs peut provoquer la disparition du symbole de sélection. Modification de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriété peut également provoquer la disparition du symbole de sélection.  
  
 Impossible de modifier la couleur et la taille du symbole de sélection.  
  
-   Si vous définissez la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> à <xref:System.Drawing.Color.White%2A>, le symbole de sélection ne seront pas visible quand un élément est sélectionné en premier.  
  
-   Si vous définissez la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> à <xref:System.Drawing.Color.Black%2A>, le symbole de sélection ne seront pas visible quand un contrôle est sélectionné, et ce symbole ne sera pas visible lorsqu’un contrôle est en mode édition.  
  
-   Si la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> est définie sur une valeur inférieure à 11, les symboles d’indicateur dans l’en-tête de l’élément ne s’affichera pas.  
  
 Vous pouvez fournir votre propre symbole en-tête et la sélection d’élément à l’aide un <xref:System.Windows.Forms.PictureBox> contrôle et surveillance le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> propriété de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> l’événement de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Guide pratique : afficher des données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : afficher les contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : modifier la disposition d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : afficher des en-têtes d’élément dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : désactiver l’ajout et la suppression d’éléments dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [Guide pratique : rechercher des données dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
