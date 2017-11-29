---
title: Data Binding in a Windows Presentation Foundation Client
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0fba3f83bbff42f570ce6da1544d2c0f1ea32393
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Data Binding in a Windows Presentation Foundation Client
Cet exemple illustre l’utilisation de la liaison de données dans un client Windows Presentation Foundation (WPF). Il utilise en outre un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui génère de manière aléatoire un tableau d'albums à retourner au client. Pour chaque album, un nom, un prix et une liste des pistes y figurant sont définis. Un nom et une durée sont indiqués pour chaque piste. Les informations retournées par le service sont liées automatiquement à l'interface utilisateur fournie par le client [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)].  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La liaison de données permet à une source de données d'être automatiquement liée à une interface utilisateur. Cela simplifie le modèle de programmation car vous n'êtes pas obligé ainsi de mettre à jour par programme chaque élément de l'interface utilisateur avec les données provenant d'un objet de données ou d'un tableau d'objets de données. Vous pouvez lier un objet à un seul élément d'interface utilisateur ou un tableau à une commande acceptant plusieurs entrées, comme `ListBox`. Le code suivant indique comment lier des données au `DataContext` d'un élément d'interface utilisateur.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 Dans l'exemple précédent, le `DataContext` de l'élément de mise en page `grid` nommé `myPanel` a pour valeur les données retournées par la méthode `GetAlbumList`. Le `DataContext` permet aux éléments d'hériter des informations de leurs éléments parents concernant la source de données utilisée pour la liaison ainsi que d'autres caractéristiques afférentes à cette dernière telles que le chemin d'accès. La ligne de code doit être exécutée à chaque mise à jour des données sur le serveur. Par exemple, cette ligne doit être exécutée lorsque la fenêtre est initialisée et lorsqu'un nouvel album est ajouté.  
  
 Dans l'exemple de code XAML suivant, `ListBox` spécifie `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Cela signifie que les données liées à l'élément d'interface utilisateur de niveau supérieur sont également liées à cette commande (c'est-à-dire au tableau d'albums). En outre, `ItemTemplate="{StaticResource AlbumStyle}"` spécifie le modèle de données à utiliser pour chaque élément dans `ListBox`. Vous pouvez également définir des modèles de données afin de spécifier les modalités de formatage des données. Ces modèles peuvent ensuite être réutilisés pour d'autres éléments d'interface utilisateur figurant dans l'application. Ces modèles présentent l'avantage d'être définis et conservés à un même emplacement.  
  
 Le modèle de données `AlbumStyle` définit une grille contenant deux `TextBlock` côte à côte. Le premier spécifie le nom de l'album et le second le nombre de pistes figurant dans cet album.  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 L'exemple de code XAML suivant crée une seconde commande `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Le code spécifie le chemin d'accès à `ItemsSource`. Cela signifie que les données liées à cette commande ne correspondent pas aux données de niveau supérieur mais à une propriété de ces données nommées `Tracks`. Cette propriété représente le tableau de pistes contenues dans l'album. Un modèle `DataTemplate` nommé `TrackStyle` est également spécifié. La mise en page du modèle `TrackStyle` est semblable à celle du modèle `AlbumStyle`, mais les `TextBlock` sont liés à des propriétés différentes. Cela est dû au fait que ces deux modèles sont utilisés avec des objets de données différents.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a>Voir aussi
