---
title: "Donn&#233;es et objets de donn&#233;es | Microsoft Docs"
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
  - "transfert de données (WPF), glisser et déposer"
  - "classe DataFormats (WPF)"
  - "classe DataObject (WPF)"
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Donn&#233;es et objets de donn&#233;es
Les données transférées dans le cadre d'une opération de glisser\-déplacer sont stockées dans un objet de données.  Conceptuellement, un objet de données se compose d'une ou plusieurs paires suivantes :  
  
-   Un <xref:System.Object> contenant les données réelles.  
  
-   Un identificateur de format de données correspondant.  
  
 Les données en elle\-même peuvent se composer de tout ce qui peut être représenté comme un <xref:System.Object>de base.  Le format de données correspondant est une chaîne ou un <xref:System.Type> qui fournit des information sur le format des données.  Les objets de données prennent en charge l'hébergement de plusieurs paires de données\/format de données, ce qui permet à un même objet de données de fournir des données dans divers formats.  
  
<a name="Data_and_Data_Objects"></a>   
## Objets de données  
 Tous les objets de données doivent implémenter l'interface <xref:System.Windows.IDataObject> qui fournit le jeu standard de méthodes suivant qui activent et facilitent le transfert de données.  
  
|Méthode|Résumé|  
|-------------|------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Récupère un objet de données dans un format de données spécifié.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Vérifie si les données sont disponibles dans un format spécifié ou peuvent être converties en un format spécifié.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Retourne une liste de formats dans lesquels sont stockées les données de cet objet de données ou vers lesquels elles peuvent être converties.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Stocke les données spécifiées dans cet objet de données.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une implémentation de base de <xref:System.Windows.IDataObject> dans la classe <xref:System.Windows.DataObject>.  La classe <xref:System.Windows.DataObject> de stock est suffisante pour de nombreux scénarios courants de transfert de données.  
  
 Il existe plusieurs formats prédéfinis, tels que bitmap, CSV, fichier, HTML, RTF, chaîne, texte et audio.  Pour plus d'informations sur les formats de données prédéfinis fournis avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez la rubrique de référence de la classe <xref:System.Windows.DataFormats>.  
  
 Les objets de données incluent couramment une fonctionnalité pour convertir automatiquement les données stockées dans un format vers un format différent pendant l'extraction des données ; cette fonctionnalité est appelée conversion automatique.  Lors de l'interrogation des formats de données disponibles dans un objet de données, les formats de données convertibles automatiquement peuvent être filtrés à partir des formats de données natifs en appelant la méthode <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> ou <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> et en affectant la valeur `false` au paramètre `autoConvert`.  Lors de l'ajout de données à un objet de données avec la méthode <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29>, la conversion automatique de données peut être interdite en affectant la valeur `false` au paramètre `autoConvert`.  
  
<a name="Working_with_Data_Objects"></a>   
## Utilisation d'objets de données  
 Cette section décrit les techniques courantes permettant de créer et d'utiliser des objets de données.  
  
### Création de nouveaux objets de données  
 La classe <xref:System.Windows.DataObject> fournit plusieurs constructeurs surchargés qui facilitent le remplissage d'une nouvelle instance de <xref:System.Windows.DataObject> avec une paire de données\/format de données unique.  
  
 L'exemple de code suivant crée un nouvel objet de données et utilise l'un des constructeurs surchargés <xref:System.Windows.DataObject.%23ctor%2A>\(<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>\) pour initialiser l'objet de données à l'aide d'une chaîne et d'un format de données spécifié.  Dans ce cas, le format de données est spécifié par une chaîne ; la classe <xref:System.Windows.DataFormats> fournit un ensemble de chaînes de type prédéfini.  La conversion automatique des données stockées est autorisée par défaut.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Pour obtenir plus d'exemples de code créant un objet de donnée, consultez [Créer un objet de données](../../../../docs/framework/wpf/advanced/how-to-create-a-data-object.md).  
  
### Stockage de données dans plusieurs formats  
 Un objet de données unique est en mesure de stocker des données dans plusieurs formats.  L'utilisation stratégique de plusieurs formats de données dans un objet de données unique rend potentiellement l'objet de données utilisable par une variété plus large de cibles de déplacement, seulement si un format de données unique pouvait être représenté.  Notez qu'en général, une source de glissement doit être agnostique concernant les formats de données utilisables par des cibles de déplacement potentielles.  
  
 L'exemple suivant indique comment utiliser la méthode <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> pour ajouter des données à un objet de données dans plusieurs formats.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### Interrogation d'un objet de données pour les formats disponibles  
 Du fait qu'un objet de données unique peut contenir un nombre arbitraire de formats de données, les objets de données comportent des fonctionnalités pour la récupération d'une liste de formats de données disponibles.  
  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetFormats%2A> pour obtenir un tableau de chaînes qui dénote tous les formats de données disponibles dans un objet de données \(à la fois natives et par conversion automatique\).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Pour obtenir plus d'exemples de code interrogeant un objet de données pour les formats de données disponibles, consultez [Répertorier les formats de données dans un objet de données](../../../../docs/framework/wpf/advanced/how-to-list-the-data-formats-in-a-data-object.md).  Pour les exemples d'interrogation d'un objet de données pour la présence d'un format de données particulier, consultez [Déterminer si un format de données est présent dans un objet de données](../../../../docs/framework/wpf/advanced/how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### Récupération des données d'un objet de données  
 La récupération des données d'un objet de donnée dans un format particulier implique simplement l'appel de l'une des méthodes <xref:System.Windows.DataObject.GetData%2A> et la spécification du format de données désiré.  L'une des méthodes <xref:System.Windows.DataObject.GetDataPresent%2A> peut être utilisée pour vérifier la présence d'un format de données particulier.  <xref:System.Windows.DataObject.GetData%2A> retourne les données dans un <xref:System.Object> ; selon le format de données, cet objet peut être casté en conteneur spécifique au type.  
  
 L'exemple de code suivant utilise la surcharge <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> pour vérifier si un format de données spécifié est disponible \(natif ou par conversion automatique\).  Si le format spécifié est disponible, l'exemple récupère les données en utilisant la méthode <xref:System.Windows.DataObject.GetData%28System.String%29>.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Pour obtenir plus d'exemples de code récupérant des données d'un objet de données, consultez [Récupérer des données dans un format de données particulier](../../../../docs/framework/wpf/advanced/how-to-retrieve-data-in-a-particular-data-format.md).  
  
### Suppression de données d'un objet de données  
 Les données ne peuvent pas être supprimées directement d'un objet de données.  Pour supprimer efficacement des données d'un objet de données, procédez comme suit :  
  
1.  Créez un nouvel objet de données qui contiendra uniquement les données vous souhaitez conserver.  
  
2.  "Copiez" les données désirées de l'ancien vers le nouvel objet de données.  Pour copier les données, utilisez l'une des méthodes <xref:System.Windows.DataObject.GetData%2A> pour récupérer un <xref:System.Object> qui contient les données brutes, puis utilisez l'une des méthodes <xref:System.Windows.DataObject.SetData%2A> pour ajouter les données au nouvel objet de données.  
  
3.  Remplacez l'ancien objet de données par le nouveau.  
  
> [!NOTE]
>  Les méthodes <xref:System.Windows.DataObject.SetData%2A> ajoutent seulement des données à un objet de données ; ils ne remplacent pas de données, même si les données et le format de données sont exactement les mêmes qu'un appel précédent.  Appeler deux fois <xref:System.Windows.DataObject.SetData%2A> pour les mêmes données et format de données en traîne un doublon de données\/format de données dans l'objet de données.