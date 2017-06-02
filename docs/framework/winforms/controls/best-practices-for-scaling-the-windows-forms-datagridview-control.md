---
title: "Meilleures pratiques pour la mise &#224; l&#39;&#233;chelle du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "meilleures pratiques, DataGridView (contrôle)"
  - "grilles de données, meilleures pratiques"
  - "DataGridView (contrôle Windows Forms), meilleures pratiques"
  - "DataGridView (contrôle Windows Forms), partage de lignes"
  - "DataGridView (contrôle Windows Forms), mettre à l'échelle"
  - "DataGridView (contrôle Windows Forms), lignes partagées"
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# Meilleures pratiques pour la mise &#224; l&#39;&#233;chelle du contr&#244;le DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> est conçu pour assurer une extensibilité maximale.  Si vous devez afficher des grandes quantités de données, vous devez suivre les directives décrites dans cette rubrique afin d'éviter de consommer de grandes quantités de mémoire ou d'affecter la réactivité de l'interface utilisateur.  Cette rubrique traite des questions suivantes :  
  
-   Utilisation efficace des styles de cellule  
  
-   Utilisation efficace des menus contextuels  
  
-   Utilisation efficace du redimensionnement automatique  
  
-   Utilisation efficace des collections de cellules, lignes et colonnes sélectionnées  
  
-   Utilisation de lignes partagées  
  
-   Empêcher les lignes de devenir non partagées  
  
 Si vous avez des besoins de performance particuliers, vous pouvez implémenter le mode virtuel et fournir vos propres opérations de gestion de données.  Pour plus d'informations, consultez [Modes d'affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).  
  
## Utilisation efficace des styles de cellule  
 Chaque cellule, ligne et colonne peut avoir ses propres informations de style.  Les informations de style sont stockées dans les objets <xref:System.Windows.Forms.DataGridViewCellStyle>.  Créer des objets du style de cellule pour de nombreux éléments <xref:System.Windows.Forms.DataGridView> individuels peut s'avérer inefficace, surtout si vous travaillez avec de grandes quantités de données.  Pour éviter d'affecter les performances, utilisez les directives suivantes :  
  
-   Évitez de définir des propriétés de style de cellule pour des objets <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewRow> individuels.  Cela inclut l'objet de ligne spécifié par la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>.  Chaque nouvelle ligne qui est clonée à partir du modèle de ligne recevra sa propre copie de l'objet de style de cellule du modèle.  Pour une extensibilité maximale, définissez les propriétés de style de cellule au niveau <xref:System.Windows.Forms.DataGridView>.  Par exemple, définissez la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> plutôt que la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>.  
  
-   Si certaines cellules nécessitent une mise en forme autre que la mise en forme par défaut, utilisez la même instance <xref:System.Windows.Forms.DataGridViewCellStyle> sur les groupes des cellules, lignes ou colonnes.  Évitez de définir directement des propriétés de type <xref:System.Windows.Forms.DataGridViewCellStyle> sur des cellules, lignes ou colonnes individuelles.  Pour obtenir un exemple de partage de style de cellule, consultez [Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  Vous pouvez également éviter une baisse de performance lorsque vous définissez les styles de cellule individuellement en gérant le gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellFormatting>.  Pour obtenir un exemple, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
-   Lorsque vous déterminez le style d'une cellule, utilisez la propriété <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=fullName> plutôt que la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>.  Accéder à la propriété <xref:System.Windows.Forms.DataGridViewCell.Style%2A> crée une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridViewCellStyle> si la propriété n'a pas déjà été utilisée.  En outre, cet objet ne peut pas contenir toutes les informations de style pour la cellule si certains styles sont hérités de la ligne, de la colonne ou du contrôle.  Pour plus d'informations sur l'héritage du style de cellule, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## Utilisation efficace des menus contextuels  
 Chaque cellule, ligne et colonne peut avoir son propre menu contextuel.  Dans le contrôle <xref:System.Windows.Forms.DataGridView>, les menus contextuels sont représentés par les contrôles <xref:System.Windows.Forms.ContextMenuStrip>.  Comme avec les objets de style de cellule, la création de menus contextuels pour de nombreux éléments <xref:System.Windows.Forms.DataGridView> individuels aura un effet négatif sur les performances.  Pour éviter cet inconvénient, suivez les directives suivantes :  
  
-   Évitez de créer des menus contextuels pour des cellules et des lignes individuelles.  Cela inclut le modèle de ligne qui est cloné avec son menu contextuel lorsque de nouvelles lignes sont ajoutées au contrôle.  Pour une extensibilité maximale, utilisez uniquement la propriété <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> du contrôle pour spécifier un menu contextuel unique pour le contrôle entier.  
  
-   Si vous avez besoin de plusieurs menus contextuels pour plusieurs lignes ou cellules, gérez les événements <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> ou <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>.  Ces événements vous permettent de gérer les objets de menu contextuel vous\-même, et vous permettent d'ajuster la performance.  
  
## Utilisation efficace du redimensionnement automatique  
 Les lignes, colonnes et en\-tête peuvent être automatiquement redimensionnées, à mesure que le contenu de la cellule change, pour que le contenu des cellules soit visible, sans être tronqué.  Changer de mode de redimensionnement permet également de redimensionner les lignes, les colonnes et les en\-têtes.  Pour déterminer la taille appropriée, le contrôle <xref:System.Windows.Forms.DataGridView> doit examiner la valeur de chaque cellule qu'il doit prendre en compte.  Lorsque vous travaillez avec de grandes quantités de données, cette analyse peut affecter négativement les performances du contrôle lors du redimensionnement automatique.  Pour éviter cet impact sur les performances, suivez les directives suivantes :  
  
-   Évitez d'utiliser le dimensionnement automatique sur un contrôle <xref:System.Windows.Forms.DataGridView> présentant une grande quantité de lignes.  Si vous utilisez le dimensionnement automatique, redimensionnez uniquement en fonction des lignes affichées.  Utilisez uniquement les lignes affichées en mode virtuel également.  
  
    -   Pour les lignes et les colonnes, utilisez le champ `DisplayedCells` ou `DisplayedCellsExceptHeaders` des énumérations <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>, <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode> et <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>.  
  
    -   Pour les en\-têtes de ligne, utilisez le champ <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> ou <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> de l'énumération <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>.  
  
-   Pour une extensibilité maximale, désactivez le dimensionnement automatique et utilisez le redimensionnement par programmation.  
  
 Pour plus d'informations, consultez [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
## Utilisation efficace des collections de cellules, lignes et colonnes sélectionnées  
 La collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> ne s'exécute pas efficacement avec les grandes sélections.  Les collections <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> peuvent également s'avérer inefficaces, bien qu'à un degré moindre, car on compte beaucoup moins de lignes que de cellules dans un contrôle <xref:System.Windows.Forms.DataGridView> classique, et beaucoup moins de colonnes que de lignes.  Pour éviter les impacts négatifs sur les performances lorsque vous travaillez avec ces collections, suivez les directives suivantes :  
  
-   Pour déterminer si toutes les cellules de la <xref:System.Windows.Forms.DataGridView> ont été sélectionnées avant que vous accédiez au contenu de la collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, vérifiez la valeur de retour de la méthode <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>.  Notez toutefois que cette méthode peut entraîner une perte du partage des lignes.  Pour plus d'informations, consultez la section suivante.  
  
-   Évitez d'utiliser la propriété <xref:System.Collections.ICollection.Count%2A> de la <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=fullName> pour déterminer le nombre de cellules sélectionnées.  À la place, utilisez la méthode <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=fullName> et passez la valeur <xref:System.Windows.Forms.DataGridViewElementStates?displayProperty=fullName>.  De la même manière, utilisez les méthodes <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=fullName> et <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=fullName> pour déterminer le nombre d'éléments sélectionnés, plutôt que d'accéder aux collections de lignes et de colonnes sélectionnées.  
  
-   Évitez les modes de sélection basés sur les cellules.  Affectez plutôt à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> ou <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName>.  
  
## Utilisation de lignes partagées  
 L'utilisation de lignes partagées permet de faire un usage efficace de la mémoire dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Les lignes partageront autant d'informations sur leur apparence et leur comportement que possible en partageant des instances de la classe <xref:System.Windows.Forms.DataGridViewRow>.  
  
 Si le partage d'instances de ligne permet d'économiser la mémoire, les lignes peuvent facilement devenir non partagées.  Par exemple, chaque fois qu'un utilisateur interagit directement avec une cellule, sa ligne n'est plus partagée.  Puisque cela est inévitable, les directives présentées dans cette rubrique sont utiles uniquement lorsque vous travaillez avec de grandes quantités de données et uniquement lorsque les utilisateurs interagissent avec une quantité relativement faible des données chaque fois que votre programme est exécuté.  
  
 Une ligne ne peut pas être partagée dans un contrôle <xref:System.Windows.Forms.DataGridView> indépendant si une de ses cellules contient des valeurs.  Lorsque le contrôle <xref:System.Windows.Forms.DataGridView> est lié à une source de données externe ou lorsque vous implémentez le mode virtuel et fournissez votre propre source de données, les valeurs des cellules sont stockées en dehors du contrôle plutôt que dans les objets de cellule, permettant aux lignes d'être partagées.  
  
 Un objet de ligne peut être partagé uniquement si l'état de toutes ses cellules peut être déterminé à partir de l'état de la ligne et de l'état des colonnes qui contiennent les cellules.  Si vous modifiez l'état d'une cellule de sorte qu'il ne puisse plus être déduit de l'état de sa ligne et de sa colonne, la ligne ne peut pas être partagée.  
  
 Par exemple, une ligne ne peut pas être partagée dans l'une des situations suivantes :  
  
-   La ligne contient une seule cellule sélectionnée qui ne se trouve pas dans une colonne sélectionnée.  
  
-   La ligne contient une cellule dont les propriétés <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> ou <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> sont définies.  
  
-   La ligne contient une <xref:System.Windows.Forms.DataGridViewComboBoxCell> dont la propriété <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> est définie.  
  
 En mode dépendant ou virtuel, vous pouvez fournir des info\-bulles et des menus contextuels pour des cellules individuelles en gérant les événements <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> et <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> essaiera automatiquement d'utiliser des lignes partagées chaque fois que des lignes sont ajoutées à la <xref:System.Windows.Forms.DataGridViewRowCollection>.  Suivez les directives suivantes pour garantir le partage des lignes :  
  
-   Évitez d'appeler la surcharge `Add(Object[])` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> et la surcharge `Insert(Object[])` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName>.  Ces surcharges créent automatiquement des lignes non partagées.  
  
-   Assurez\-vous que la ligne spécifiée dans la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName> peut être partagée dans les cas suivants :  
  
    -   En cas d'appel de la surcharge `Add()` ou `Add(Int32)` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> ou de la surcharge `Insert(Int32,Int32)` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName>.  
  
    -   En cas d'augmentation de la valeur de la propriété <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=fullName>.  
  
    -   En cas de définition de la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>.  
  
-   Veillez à ce que la ligne indiquée par le paramètre `indexSource` puisse être partagée lors de l'appel des méthodes <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A> et <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName>.  
  
-   Veillez à ce que la ou les lignes spécifiées puissent être partagées lors de l'appel de la surcharge `Add(DataGridViewRow)` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>, de la surcharge `Insert(Int32,DataGridViewRow)` de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>, et de la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName>.  
  
 Pour déterminer si une ligne est partagée, utilisez la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName> pour récupérer l'objet de ligne, puis vérifiez la propriété <xref:System.Windows.Forms.DataGridViewBand.Index%2A> de l'objet.  Les lignes partagées ont toujours une valeur de propriété <xref:System.Windows.Forms.DataGridViewBand.Index%2A> de \-1.  
  
## Empêcher les lignes de devenir non partagées  
 Les lignes partagées peuvent devenir non partagées à la suite d'une action du code ou de l'utilisateur.  Pour éviter un impact négatif sur les performances, vous devez éviter de provoquer une perte du partage des lignes.  Pendant le développement d'applications, vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.RowUnshared> pour déterminer à quel moment les lignes deviennent non partagées.  Cela est utile en cas de débogage de problèmes de partage de ligne.  
  
 Pour empêcher les lignes de devenir non partagées, suivez les directives suivantes :  
  
-   Évitez indexer la collection <xref:System.Windows.Forms.DataGridView.Rows%2A> ou d'itérer en son sein à l'aide d'une boucle `foreach`.  Il n'est en général pas nécessaire d'accéder directement aux lignes.  Les méthodes <xref:System.Windows.Forms.DataGridView> qui fonctionnent sur les lignes prennent des arguments d'index de ligne plutôt que des instances de ligne.  En outre, les gestionnaires d'événements de ligne reçoivent des objets d'argument d'événement avec des propriétés de ligne que vous pouvez utiliser pour manipuler des lignes sans qu'elles deviennent non partagées.  
  
-   Si vous devez accéder à un objet de ligne, utilisez la méthode <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName> et passez l'index réel de la ligne.  Notez toutefois que la modification d'un objet de ligne partagé récupéré à l'aide de cette méthode modifiera toutes les lignes qui partagent cet objet.  La ligne des nouveaux enregistrements n'est cependant pas partagée avec d'autres lignes pour qu'elle ne soit pas affectée par la modification d'une autre ligne.  Notez également que différentes lignes représentées par une ligne partagée peuvent avoir des menus contextuels différents.  Pour récupérer le menu contextuel correct à partir d'une instance de ligne partagée, utilisez la méthode <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> et passez l'index réel de la ligne.  Si vous accédez à la place à la propriété <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> de la ligne partagée, l'index de ligne partagé \-1 sera utilisé et le menu contextuel correct ne sera pas récupéré.  
  
-   Évitez d'indexer la collection <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=fullName>.  Si vous accédez directement à une cellule, sa ligne parente devient non partagée, instanciant une nouvelle <xref:System.Windows.Forms.DataGridViewRow>.  Les gestionnaires d'événements de cellule reçoivent des objets d'argument d'événement avec des propriétés de cellule que vous pouvez utiliser pour manipuler des cellules sans que les lignes deviennent non partagées.  Vous pouvez également utiliser la propriété <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> pour récupérer les index de ligne et de colonne de la cellule active sans accéder directement à la cellule.  
  
-   Évitez les modes de sélection basés sur les cellules.  Avec ces modes, les lignes deviennent non partagées.  Affectez plutôt à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> ou <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName>.  
  
-   Ne gérez pas les événements <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=fullName> ou <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=fullName>.  Avec ces événements, les lignes deviennent non partagées.  Par ailleurs, n'appelez pas les méthodes <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=fullName> ou <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=fullName>, qui déclenchent ces événements.  
  
-   N'accédez pas à la collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=fullName> lorsque la valeur de la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> est <xref:System.Windows.Forms.DataGridViewSelectionMode>, <xref:System.Windows.Forms.DataGridViewSelectionMode>, <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>.  Si vous le faites, toutes les lignes sélectionnées deviennent non partagées.  
  
-   N'appelez pas la méthode <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=fullName>.  Avec cette méthode, les lignes deviennent non partagées.  
  
-   N'appelez pas la méthode <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=fullName> lorsque la valeur de la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> est <xref:System.Windows.Forms.DataGridViewSelectionMode>.  Si vous le faites, toutes les lignes deviennent non partagées.  
  
-   N'affectez pas à la propriété <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> ou <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> d'une cellule la valeur `false` lorsque la propriété correspondante dans sa colonne a la valeur `true`.  Si vous le faites, toutes les lignes deviennent non partagées.  
  
-   N'utilisez pas la propriété <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=fullName>.  Si vous le faites, toutes les lignes deviennent non partagées.  
  
-   N'appelez pas la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>.  Si vous triez avec un comparateur personnalisé, toutes les lignes deviennent non partagées.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [Réglage des performances dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [Modes d'affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Comment : définir les styles de cellules par défaut pour le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)   
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)