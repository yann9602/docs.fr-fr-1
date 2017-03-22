---
title: "Introduction au contrôle DataRepeater (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86078426494caabefc6bbfb036037007e830e1cb
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>Introduction au contrôle DataRepeater (Visual Studio)
Visual Basic Power Packs <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle est un conteneur à défilement répété de contrôles qui affichent des données, par exemple, des lignes dans une table de base de données.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Il peut être utilisé comme alternative à le <xref:System.Windows.Forms.DataGridView>contrôle lorsque vous avez besoin d’un meilleur contrôle sur la disposition des données.</xref:System.Windows.Forms.DataGridView> Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>« répète » d’un groupe de contrôles connexes en créant plusieurs instances dans une vue de défilement.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Cela permet aux utilisateurs d’afficher plusieurs enregistrements en même temps.  
  
## <a name="overview"></a>Vue d'ensemble  
 Au moment du design, la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle se compose de deux sections.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> La section externe correspond à la *viewport*, où les données de défilement seront affiche au moment de l’exécution. La section interne (supérieur), appelée la *modèle d’élément*, est l’endroit où vous positionnez des contrôles qui seront répétés au moment de l’exécution, en général, un contrôle pour chaque champ dans la source de données. Les propriétés et les contrôles dans le modèle d’élément sont encapsulés dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>propriété.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>  
  
 Au moment de l’exécution, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>est copié vers un ordinateur virtuel, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>objet qui est utilisé pour afficher les données lors de chaque enregistrement est affiché.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> Vous pouvez personnaliser l’affichage d’enregistrements individuels dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>événement, par exemple, mettre en surbrillance un champ en fonction de la valeur qu’il contient.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Pour plus d’informations, consultez [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 L’utilisation la plus courante pour un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle consiste à afficher les données d’une table de base de données ou une autre source de données liée.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> En plus de [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] des objets de données, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle peut être lié à toute classe qui implémente le <xref:System.Collections.IList>interface (y compris les tableaux), toute classe qui implémente le <xref:System.ComponentModel.IListSource>de l’interface, toute classe qui implémente le <xref:System.ComponentModel.IBindingList>interface ou toute classe qui implémente le <xref:System.ComponentModel.IBindingListView>interface.</xref:System.ComponentModel.IBindingListView> </xref:System.ComponentModel.IBindingList> </xref:System.ComponentModel.IListSource> </xref:System.Collections.IList> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
### <a name="data-binding"></a>Liaison de données  
 En règle générale, vous effectuer la liaison de données en faisant glisser des champs à partir de la **des Sources de données** fenêtre sur la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Pour plus d’informations, consultez [Comment : afficher des données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Lorsque vous travaillez avec de grandes quantités de données, vous pouvez définir le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriété `True` pour afficher un sous-ensemble des données disponibles.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> Mode virtuel requiert l’implémentation d’un cache de données à partir de laquelle le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>est remplie, et vous devez contrôler toutes les interactions avec le cache de données en cours d’exécution.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Pour plus d’informations, consultez [Mode virtuel dans le contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Vous pouvez également afficher des contrôles indépendants sur un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Par exemple, vous pouvez afficher une image qui est répétée sur chaque élément. Pour plus d’informations, consultez [Comment : afficher des contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Événements  
 Les événements les plus importants pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle sont le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>événement qui est déclenché lorsque de nouveaux éléments défilent dans l’affichage, et le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>événement qui est déclenché lorsqu’un élément est sélectionné.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Vous pouvez utiliser la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>pour modifier l’apparence de l’élément.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Par exemple, vous pouvez mettre en surbrillance les valeurs négatives. Utilisez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>événement pour accéder aux valeurs des contrôles lorsqu’un élément est sélectionné.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>  
  
 Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle expose tous les événements de contrôle standard dans l’éditeur de Code.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Toutefois, certains événements ne doivent pas utilisés. Clavier et souris tels que des événements `KeyDown`, `Click`, et `MouseDown` ne seront pas déclenchés au moment de l’exécution car le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle lui-même n’a jamais le focus.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
 Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>n’expose pas d’événements au moment du design, car il est créé uniquement au moment de l’exécution.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Si vous souhaitez gérer les événements de clavier et de la souris, vous pouvez ajouter un <xref:System.Windows.Forms.Panel>le contrôle à la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>au moment du design, puis gérer les événements pour le <xref:System.Windows.Forms.Panel>.</xref:System.Windows.Forms.Panel> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:System.Windows.Forms.Panel> Pour plus d’informations, consultez [dépannage du contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Personnalisations  
 Il existe de nombreuses façons de personnaliser l’apparence et le comportement de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler, à la fois au moment de l’exécution et au moment du design.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Propriétés peuvent être définies pour modifier les couleurs, masquer ou modifier les en-têtes d’élément, modifiez l’orientation de vertical à horizontal et bien plus encore. Pour plus d’informations, consultez [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [Comment : afficher les en-têtes d’élément dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), et [Comment : modifier la disposition d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Notez que certaines propriétés s’appliquent pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle lui-même, tandis que d’autres s’appliquent uniquement au serveur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Assurez-vous que vous disposez de la section appropriée du contrôle sélectionné avant de définir des propriétés. Pour plus d’informations, consultez [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Autres personnalisations incluent contrôler la capacité d’ajouter ou supprimer des enregistrements, l’ajout de fonctionnalités de recherche et affichage de données connexes dans un format maître / détail. Pour plus d’informations, consultez [Comment : désactiver l’ajout et la suppression d’éléments DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [Comment : rechercher des données dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), et [Comment : créer un formulaire maître/détail à l’aide de deux contrôles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [Procédure pas à pas : Affichage des données dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
