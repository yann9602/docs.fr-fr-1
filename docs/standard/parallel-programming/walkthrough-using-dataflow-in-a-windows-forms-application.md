---
title: "Procédure pas à pas : utilisation de flux de données dans une application Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2775cc99020fd99d6e7d79cdf3e1ffcc3219146
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Procédure pas à pas : utilisation de flux de données dans une application Windows Forms
Ce document montre comment créer un réseau de blocs de flux de données qui effectuent un traitement des images dans une application Windows Forms.  
  
 Dans cet exemple, on charge des fichiers image à partir du dossier spécifié, on crée une image composite, et on affiche le résultat. L’exemple utilise le modèle de flux de données pour acheminer les images via le réseau. Dans le modèle de flux de données, les composants indépendants d’un programme communiquent entre eux en envoyant des messages. Lorsqu’un composant reçoit un message, il effectue une action, puis transmet le résultat à un autre composant. Comparez cela avec le modèle de flux de contrôle, dans lequel une application utilise des structures de contrôle (par exemple, des instructions conditionnelles, des boucles, etc.) pour contrôler l’ordre des opérations dans un programme.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Lisez la rubrique [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) avant de démarrer cette procédure pas à pas.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
 
  
## <a name="sections"></a>Sections  
 Cette procédure pas à pas contient les sections suivantes :  
  
-   [Création de l’application Windows Forms](#winforms)  
  
-   [Création du réseau de flux de données](#network)  
  
-   [Connexion du réseau de flux de données à l’interface utilisateur](#ui)  
  
-   [Exemple complet](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Création de l’application Windows Forms  
 Cette section décrit comment créer l’application Windows Forms de base et ajouter des contrôles au formulaire principal.  
  
#### <a name="to-create-the-windows-forms-application"></a>Pour créer une Application Windows Forms  
  
1.  Dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], créez un projet [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ou un projet d’**application Windows Forms** Visual Basic. Dans ce document, le projet est nommé `CompositeImages`.  
  
2.  Dans le Concepteur de formulaires pour le formulaire principal, Form1.cs (Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ajoutez un <xref:System.Windows.Forms.ToolStrip> contrôle.  
  
3.  Ajouter un <xref:System.Windows.Forms.ToolStripButton> le contrôle à la <xref:System.Windows.Forms.ToolStrip> contrôle. Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> et <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété **choisir le dossier**.  
  
4.  Ajoutez un deuxième <xref:System.Windows.Forms.ToolStripButton> le contrôle à la <xref:System.Windows.Forms.ToolStrip> contrôle. Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, le <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété **Annuler**et le <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> propriété `False`.  
  
5.  Ajouter un <xref:System.Windows.Forms.PictureBox> objet au formulaire principal. Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Création du réseau de flux de données  
 Cette section décrit comment créer le réseau de flux de données qui effectue le traitement des images.  
  
#### <a name="to-create-the-dataflow-network"></a>Pour créer le réseau de flux de données  
  
1.  Dans votre projet, ajoutez une référence à System.Threading.Tasks.Dataflow.dll.  
  
2.  Vérifiez que Form1.cs (Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contient les instructions `using` suivantes (`Using` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) :  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  Ajoutez les membres de données suivants à la classe `Form1` :  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  Ajoutez la méthode `CreateImageProcessingNetwork` suivante à la classe `Form1`. Cette méthode crée le réseau de traitement des images.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  Implémentez la méthode `LoadBitmaps`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  Implémentez la méthode `CreateCompositeBitmap`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  La version c# de le `CreateCompositeBitmap` méthode utilise des pointeurs pour permettre un traitement efficace de la <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objets. Par conséquent, vous devez activer l’option **Autoriser les blocs de code unsafe** dans votre projet pour pouvoir utiliser le mot-clé [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md). Pour plus d’informations sur l’activation du code unsafe dans une [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] projet d’équipe, consultez [Build Page, Project Designer (c#)] https://msdn.microsoft.com/library/kb4wyys2).  
  
 Le tableau ci-dessous décrit les membres du réseau.  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Prend un chemin d’accès du dossier en tant qu’entrée et produit une collection de <xref:System.Drawing.Bitmap> objets en tant que sortie.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Accepte une collection de <xref:System.Drawing.Bitmap> des objets comme entrée et produit un bitmap composite en tant que sortie.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Affiche l’image bitmap composite sur le formulaire.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Affiche une image pour indiquer que l’opération est annulée et permet à l’utilisateur de sélectionner un autre dossier.|  
  
 Pour connecter les blocs de flux de données pour former un réseau, cet exemple utilise le <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> (méthode). Le <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> méthode contient une version surchargée qui accepte un <xref:System.Predicate%601> objet qui détermine si le bloc cible accepte ou rejette un message. Ce mécanisme de filtrage permet aux blocs de messages de ne recevoir que certaines valeurs. Dans cet exemple, le réseau peut créer une branche de deux manières. La branche principale charge les images à partir du disque, crée l’image composite et affiche cette image sur le formulaire. L’autre branche annule l’opération en cours. Le <xref:System.Predicate%601> objets activer les blocs de flux de données le long de la branche principale pour basculer vers l’autre branche en rejetant certains messages. Par exemple, si l’utilisateur annule l’opération, le bloc de flux de données `createCompositeBitmap` produit `null` (`Nothing` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) comme sortie. Le bloc de flux de données `displayCompositeBitmap` rejette les valeurs d’entrée `null`. Par conséquent, le message est proposé aux `operationCancelled`. Le bloc de flux de données `operationCancelled` accepte tous les messages. Par conséquent, il affiche une image pour indiquer que l’opération est annulée.  
  
 L'illustration suivante montre le réseau de traitement des images.  
  
 ![Le réseau de traitement des images](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 Étant donné que les blocs de flux de données `displayCompositeBitmap` et `operationCancelled` agissent sur l’interface utilisateur, il est important que ces actions se produisent sur le thread de l’interface utilisateur. Pour ce faire, pendant la construction, chacun de ces objets fournit un <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> objet ayant la <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> propriété <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. La méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> crée un objet <xref:System.Threading.Tasks.TaskScheduler> qui effectue le travail dans le contexte actuel de synchronisation. Étant donné que la méthode `CreateImageProcessingNetwork` est appelée à partir du gestionnaire du bouton **Choisir le dossier**, qui est exécuté sur le thread de l’interface utilisateur, les actions des blocs de flux de données `displayCompositeBitmap` et `operationCancelled` sont également exécutées sur le thread de l’interface utilisateur.  
  
 Cet exemple utilise un jeton d’annulation partagé au lieu de définir la <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriété, car le <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> propriété définitivement annulé l’exécution du bloc de flux de données. Cet exemple explique comment un jeton d’annulation permet de réutiliser un réseau de flux de données plusieurs fois, même lorsque l’utilisateur annule une ou plusieurs opérations. Pour obtenir un exemple qui utilise <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> pour annuler définitivement l’exécution d’un bloc de flux de données, consultez [Comment : annuler un Dataflow Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Connexion du réseau de flux de données à l’interface utilisateur  
 Cette section décrit comment connecter le réseau de flux de données à l’interface utilisateur. La création de l’image composite et l’annulation de l’opération sont lancées à partir des boutons **Choisir le dossier** et **Annuler**. Lorsque l’utilisateur clique sur l’un de ces boutons, l’action appropriée est lancée de manière asynchrone.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Connecter le réseau de flux de données à l’interface utilisateur  
  
1.  Dans le Concepteur de formulaires pour le formulaire principal, créez un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> événement pour le **choisir le dossier** bouton.  
  
2.  Implémentez la <xref:System.Windows.Forms.ToolStripItem.Click> événement pour le **choisir le dossier** bouton.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  Dans le Concepteur de formulaires pour le formulaire principal, créez un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> événement pour le **Annuler** bouton.  
  
4.  Implémentez la <xref:System.Windows.Forms.ToolStripItem.Click> événement pour le **Annuler** bouton.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Exemple complet  
 L'exemple suivant présente le code complet pour cette visite.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 L’illustration suivante montre une sortie type du dossier \Échantillons d'images\.  
  
 ![L’application Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
