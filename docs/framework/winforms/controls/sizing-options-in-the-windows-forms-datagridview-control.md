---
title: "Options de dimensionnement dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, dimensionnement des colonnes"
  - "grilles de données, dimensionner les lignes"
  - "grilles de données, options de dimensionnement"
  - "DataGridView (contrôle Windows Forms), dimensionnement des colonnes"
  - "DataGridView (contrôle Windows Forms), dimensionner les lignes"
  - "DataGridView (contrôle Windows Forms), options de dimensionnement"
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Options de dimensionnement dans le contr&#244;le DataGridView Windows Forms
Les lignes, colonnes et en\-têtes de <xref:System.Windows.Forms.DataGridView> peuvent changer de taille à la suite de nombreuses occurrences différentes.  Le tableau suivant indique ces occurrences.  
  
|Occurrence|Description|  
|----------------|-----------------|  
|Redimensionnement par l'utilisateur|Les utilisateurs peuvent changer la taille des lignes, colonnes ou en\-têtes en faisant glisser ou en double\-cliquant sur les séparateurs.|  
|Redimensionnement des contrôles|En mode de remplissage de colonne, les largeurs de colonne changent lorsque la largeur du contrôle change. Par exemple, lorsque le contrôle est ancré à son formulaire parent et que l'utilisateur redimensionne le formulaire.|  
|Modification de valeur de la cellule|En mode de dimensionnement automatique basé sur le contenu, les tailles changent pour s'adapter aux nouvelles valeurs affichées.|  
|Appel de méthode|Le redimensionnement par programme basé sur le contenu vous permet d'effectuer des réglages de taille opportunistes en fonction des valeurs des cellules au moment de l'appel de la méthode.|  
|Définition de propriété|Vous pouvez également définir des valeurs de hauteur et de largeur spécifiques.|  
  
 Par défaut, le redimensionnement utilisateur est activé, le dimensionnement automatique est désactivé et les valeurs de cellule qui sont plus larges que leurs colonnes sont tronquées.  
  
 Le tableau suivant affiche des scénarios que vous pouvez utiliser pour ajuster le comportement par défaut ou pour utiliser des options de dimensionnement spécifiques vous permettant d'obtenir des effets particuliers.  
  
|Scénario|Implémentation|  
|--------------|--------------------|  
|Utilisez le mode de remplissage de colonne pour afficher des données de taille similaire dans un nombre relativement limité de colonnes qui occupent toute la largeur du contrôle sans afficher de barre de défilement horizontale.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>.|  
|Utilisez le mode de remplissage de colonne avec des valeurs d'affichage de tailles variables.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>.  Initialisez des largeurs de colonne relatives en définissant les propriétés <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> de la colonne ou en appelant la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> du contrôle après avoir rempli le contrôle de données.|  
|Utilisez le mode de remplissage de colonne avec des valeurs d'importance variable.|Affectez à la propriété <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>.  Définissez des valeurs <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> importantes pour les colonnes qui doivent toujours afficher une partie de leurs données ou utilisez une option de dimensionnement autre que le mode de remplissage pour des colonnes spécifiques.|  
|Utilisez le mode de remplissage de colonne pour éviter d'afficher l'arrière\-plan du contrôle.|Donnez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> de la dernière colonne la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> et utilisez d'autres options de dimensionnement pour les autres colonnes.  Si les autres colonnes utilisent une partie trop importante de l'espace disponible, définissez la propriété <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> de la dernière colonne.|  
|Affichez une colonne à largeur fixe, comme une colonne d'icône ou d'ID.|Donnez à <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> et à <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> la valeur <xref:System.Windows.Forms.DataGridViewTriState> pour la colonne.  Initialisez sa largeur en définissant la propriété <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> ou en appelant la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> du contrôle après avoir rempli le contrôle de données.|  
|Ajustez automatiquement les tailles chaque fois que le contenu de la cellule change pour éviter de tronquer les données et optimiser l'utilisation de l'espace.|Définissez une propriété de dimensionnement automatique à l'aide d'une valeur qui représente un mode de dimensionnement basé sur contenu.  Pour éviter un impact négatif sur les performances lorsque vous travaillez avec de grandes quantités de données, utilisez un mode de dimensionnement qui calcule uniquement les lignes affichées.|  
|Ajustez les tailles en fonction des valeurs contenues dans les lignes affichées pour éviter d'affecter négativement les performances lorsque vous travaillez avec une grande quantité de lignes.|Utilisez des valeurs d'énumération de mode de dimensionnement appropriées en mode de dimensionnement automatique ou par programme.  Pour ajuster les tailles en fonction des valeurs dans les lignes qui s'affichent à mesure que vous les faites défiler, appelez une méthode de redimensionnement dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.Scroll>.  Pour personnaliser le redimensionnement par double\-clic de l'utilisateur de sorte que seules les valeurs les lignes affichées déterminent les nouvelles tailles, appelez une méthode de redimensionnement dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> ou <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>.|  
|Ajustez les tailles en fonction du contenu des cellules à des moments spécifiques pour éviter les impacts négatifs sur les performances ou permettre le redimensionnement par l'utilisateur.|Appelez une méthode de redimensionnement basée sur contenu dans un gestionnaire d'événements.  Par exemple, utilisez l'événement <xref:System.Windows.Forms.DataGridView.DataBindingComplete> pour initialiser les tailles après la liaison et gérez l'événement <xref:System.Windows.Forms.DataGridView.CellValidated> ou <xref:System.Windows.Forms.DataGridView.CellValueChanged> pour ajuster des tailles en compensation des modifications utilisateur dans une source de données liée.|  
|Ajustez les hauteurs de lignes pour les contenus de cellule multilignes.|Veillez à ce que la largeur des colonnes soit suffisante pour afficher les paragraphes de texte et utilisez le dimensionnement de ligne basé sur contenu automatique ou par programme pour régler les hauteurs.  Veillez également à ce que les cellules à contenu multiligne soient affichées à l'aide dans un style de cellule <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> d'une valeur de <xref:System.Windows.Forms.DataGridViewTriState>.<br /><br /> En général, vous utiliserez un mode de dimensionnement de colonne automatique pour maintenir des largeurs de colonne ou les définir à des largeurs spécifiques avant que les hauteurs de ligne soient ajustées.|  
  
## Redimensionnement à l'aide de la souris  
 Par défaut, les utilisateurs peuvent redimensionner les lignes, colonnes et en\-têtes qui n'utilisent pas de mode de dimensionnement automatique basé sur les valeurs des cellules.  Pour empêcher les utilisateurs de redimensionner dans d'autres modes, tels que le mode du remplissage de colonne, définissez une ou plusieurs des propriétés <xref:System.Windows.Forms.DataGridView> suivantes :  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Vous pouvez également empêcher les utilisateurs de redimensionner des lignes ou des colonnes en définissant leurs propriétés <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>.  Par défaut, la valeur de la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> dépend de la valeur de la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> pour les colonnes et de la valeur de la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> pour les lignes.  Toutefois, si vous affectez explicitement à <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> la valeur <xref:System.Windows.Forms.DataGridViewTriState> ou <xref:System.Windows.Forms.DataGridViewTriState>, la valeur spécifiée substitue la valeur du contrôle pour cette ligne ou colonne.  Affectez la valeur <xref:System.Windows.Forms.DataGridViewTriState> à <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> pour restaurer l'héritage.  
  
 Comme <xref:System.Windows.Forms.DataGridViewTriState> restaure l'héritage de valeur, la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> ne retournera jamais la valeur <xref:System.Windows.Forms.DataGridViewTriState> à moins que la ligne ou la colonne ne soit ajoutée à un contrôle <xref:System.Windows.Forms.DataGridView>.  Si vous devez déterminer si la valeur de la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> d'une ligne ou colonne est héritée, examinez sa propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A>.  Si la valeur <xref:System.Windows.Forms.DataGridViewElement.State%2A> inclut l'indicateur <xref:System.Windows.Forms.DataGridViewElementStates>, la valeur de la propriété <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> n'est pas héritée.  
  
## Dimensionnement automatique  
 Il existe deux types de dimensionnement automatique dans le contrôle <xref:System.Windows.Forms.DataGridView> : le mode de remplissage de colonne et le dimensionnement automatique basé sur contenu.  
  
 En mode de remplissage de colonne, les colonnes visibles du contrôle remplissent la largeur de la zone d'affichage du contrôle.  Pour plus d'informations sur ce mode, consultez [Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Vous pouvez également configurer les lignes, colonnes et en\-tête de sorte qu'ils ajustent automatiquement leurs tailles en fonction de leur contenu de cellule.  Dans ce cas, le réglage de la taille se produit à chaque changement du contenu des cellules.  
  
> [!NOTE]
>  Si vous conservez des valeurs de cellules dans un cache de données personnalisé à l'aide du mode virtuel, le dimensionnement automatique se produit lorsque l'utilisateur modifie une valeur de cellule, mais pas lorsque vous modifiez une valeur mise en cache en dehors d'un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellValuePushed>.  Dans ce cas, appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> pour forcer le contrôle à mettre à jour l'affichage des cellules et appliquer les modes actuels de dimensionnement automatique.  
  
 Si le dimensionnement automatique basé sur contenu est activé pour une seule dimension \(c'est\-à\-dire pour les lignes, mais pas pour les colonnes, ou pour les colonnes, mais pas pour les lignes\) et que <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est également activé, le réglage de la taille se produit également chaque fois que l'autre dimension change.  Par exemple, si les lignes \- pas les colonnes \- sont configurées pour le dimensionnement automatique et que <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est activé, les utilisateurs peuvent faire glisser les séparateurs des colonnes pour modifier la largeur d'une colonne et les hauteurs de ligne s'ajusteront automatiquement pour que le contenu des cellules reste complètement visible.  
  
 Si les lignes et les colonnes sont configurées pour le dimensionnement automatique basé sur contenu et que <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> est activé, le contrôle <xref:System.Windows.Forms.DataGridView> ajustera les tailles à chaque changement de contenu des cellules et appliquera un rapport hauteur\-largeur de cellule idéal pour calculer les nouvelles tailles.  
  
 Pour configurer le mode de dimensionnement pour les en\-têtes et les lignes et pour les colonnes qui ne substituent pas la valeur du contrôle, définissez une ou plusieurs des propriétés <xref:System.Windows.Forms.DataGridView> suivantes :  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Pour substituer le mode de dimensionnement des colonnes du contrôle sur une colonne particulière, donnez à sa propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> une valeur autre que <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>.  Le mode de dimensionnement pour une colonne est en fait déterminé par sa propriété <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>.  La valeur de cette propriété est basée sur la valeur de la propriété <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> de la colonne sauf si cette valeur est <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>, auquel cas la valeur <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> du contrôle est héritée.  
  
 Utilisez le redimensionnement automatique basé sur contenu avec prudence lorsque vous travaillez avec de grandes quantités de données.  Pour éviter d'affecter négativement les performances, utilisez des modes de dimensionnement automatique qui calculent les tailles en se basant uniquement sur les lignes affichées plutôt qu'analyser toutes les lignes du contrôle.  Pour une performance maximale, utilisez plutôt le redimensionnement par programme qui vous permet de redimensionner à des moments spécifiques, par exemple immédiatement après le chargement de nouvelles données.  
  
 Les modes de dimensionnement automatique basés sur contenu n'affectent pas les lignes, les colonnes ou les en\-têtes que vous avez masqués en affectant la valeur `false` à la propriété <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> de la ligne ou de la colonne ou aux propriétés <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> ou <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> du contrôle.  Par exemple, si une colonne est masquée après avoir été automatiquement dimensionnée pour s'adapter à une valeur de cellule de grande taille, la colonne masquée ne changera pas de taille si la ligne qui contient la grande valeur de cellule est supprimée.  Le dimensionnement automatique n'est pas affecté par les changements de visibilité. Ainsi, redonner à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> de la colonne la valeur `true` ne l'obligera pas à recalculer sa taille en fonction de son contenu actuel.  
  
 Le redimensionnement par programme basé sur contenu affecte les lignes, les colonnes et les en\-têtes indépendamment de leur visibilité.  
  
## Redimensionnement par programmation  
 Lorsque le dimensionnement automatique est désactivé, vous pouvez définir par programme la largeur ou la hauteur exactes des lignes, colonnes ou en\-tête à l'aide des propriétés suivantes :  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>  
  
 Vous pouvez également redimensionner par programme les lignes, colonnes et en\-tête en fonction de leur contenu à l'aide des méthodes suivantes :  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Ces méthodes redimensionneront les lignes, colonnes ou en\-tête une fois plutôt que de les configurer en vue d'un redimensionnement continu.  Les nouvelles tailles sont calculées automatiquement pour afficher le contenu d'une cellule sans qu'il soit tronqué.  Toutefois, lorsque vous redimensionnez par programme des colonnes dont la propriété <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>, les largeurs basées sur le contenu calculées sont utilisées pour ajuster proportionnellement les valeurs de la propriété <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> des colonnes. Les largeurs de colonne réelles sont ensuite calculées sur la base de ces nouvelles proportions afin que toutes les colonnes remplissent la zone d'affichage disponible du contrôle.  
  
 Le redimensionnement par programmation est utile pour éviter l'impact négatif sur les performances qu'engendre le redimensionnement continu.  Il est également utile pour fournir des tailles initiales pour les lignes, colonnes et en\-têtes redimensionnables par l'utilisateur, et pour le mode de remplissage de colonne.  
  
 En règle générale, vous appellerez les méthodes de redimensionnement par programmation à des moments spécifiques.  Par exemple, vous pouvez redimensionner par programme toutes les colonnes immédiatement après avoir chargé des données, ou redimensionner par programme une ligne spécifique après qu'une valeur d'une cellule donnée a été modifiée.  
  
## Personnalisation du comportement du dimensionnement basé sur contenu  
 Vous pouvez personnaliser les comportements de dimensionnement lorsque vous travaillez avec des types de cellule, ligne, et colonne <xref:System.Windows.Forms.DataGridView> dérivés en substituant les méthodes <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=fullName>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=fullName> ou <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=fullName> ou en appelant des surcharges de méthodes de redimensionnement protégées dans un contrôle <xref:System.Windows.Forms.DataGridView> dérivé.  Les surcharges de méthode de redimensionnement protégées sont conçues pour travailler en paires pour obtenir un rapport hauteur\-largeur de cellule idéal, qui évite les hauteurs ou largeurs de cellules démesurées.  Par exemple, si vous appelez la surcharge `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` de la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> et passez la valeur `false` pour le paramètre <xref:System.Boolean>, la surcharge calculera les hauteurs et largeurs idéales pour les cellules de la ligne, mais ajustera uniquement les hauteurs de ligne.  Vous devez appeler ensuite la méthode <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> pour ajuster les largeurs de colonne à la valeur idéale calculée.  
  
## Options de dimensionnement basées sur contenu  
 Les énumérations utilisées par les propriétés et les méthodes de dimensionnement ont des valeurs semblables pour le dimensionnement basé sur contenu.  Avec ces valeurs, vous pouvez limiter les cellules qui sont utilisées pour calculer les tailles par défaut.  Pour toutes les énumérations de dimensionnement, les valeurs dont les noms font référence aux cellules affichées limitent leurs calculs aux cellules des lignes affichées.  L'exclusion de lignes est utile pour éviter d'affecter négativement les performances si vous travaillez avec de grandes quantités de lignes.  Vous pouvez également limiter les calculs aux valeurs des cellules ou aux cellules n'appartenant pas à l'en\-tête.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>   
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>   
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>   
 [Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)   
 [Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)   
 [Comment : définir les modes de redimensionnement du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)