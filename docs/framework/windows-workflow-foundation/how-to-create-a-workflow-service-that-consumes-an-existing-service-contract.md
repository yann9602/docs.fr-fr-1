---
title: "Proc&#233;dure&#160;: cr&#233;er un service de workflow qui utilise un contrat de service existant | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: cr&#233;er un service de workflow qui utilise un contrat de service existant
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] offre une meilleure intégration entre les services Web et les workflows sous la forme du développement de workflow contrat en premier.L'outil de développement de workflow Contrat en premier vous permet de concevoir le contrat dans le code en premier.L'outil génère automatiquement un modèle d'activité dans la boîte à outils pour les opérations du contrat.  
  
> [!NOTE]
>  Cette rubrique fournit des instructions pas à pas pour créer un service de workflow contrat en premier.[!INCLUDE[crabout](../../../includes/crabout-md.md)] le développement de services de workflow « contrat en premier », consultez [Développement de services de workflow « contrat en premier »](../../../docs/framework/windows-workflow-foundation//contract-first-workflow-service-development.md).  
  
### Création du projet de workflow  
  
1.  Dans [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], sélectionnez **Fichier**, **Nouveau projet**.Sélectionnez le nœud **WCF** sous le nœud **C\#** dans l'arborescence **Modèles** , puis sélectionnez le modèle **Application de service de workflow WCF**.  
  
2.  Nommez le nouveau projet `ContractFirst`, puis cliquez sur **OK**.  
  
### Création du contrat de service  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**, **Nouvel élément...**.Sélectionnez le nœud **Code** à gauche, et le modèle **Classe** à droite.Nommez la nouvelle classe `IBookService`, puis cliquez sur **OK**.  
  
2.  En haut de la fenêtre de code qui apparaît, ajoutez une instruction Using à `System.Servicemodel`.  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  Remplacez la définition d'exemple de classe par la définition d'interface suivante.  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  Générez le projet en appuyant sur **Ctrl\+Maj\+B**.  
  
### Importation du contrat de service  
  
1.  Cliquez avec le bouton droit sur le projet dans l'**Explorateur de solutions** et sélectionnez **Importer le contrat de service**.Sous **\<Projet actif\>**, ouvrez tous les sous\-nœuds et sélectionnez **IBookService**.Cliquez sur **OK**.  
  
2.  Une boîte de dialogue s'ouvre indiquant que l'opération s'est achevée avec succès et que les activités personnalisées générées s'afficheront dans la boîte à outils une fois le projet construit.Cliquez sur **OK**.  
  
3.  Générez le projet en appuyant sur **Ctrl\+Maj\+B**, afin que les activités importées s'affichent dans la boîte à outils.  
  
4.  Dans l'**Explorateur de solutions**, ouvrez Service1.xamlx.Le service de workflow apparaît dans le concepteur.  
  
5.  Sélectionnez l'activité **Séquence**.Dans la fenêtre Propriétés, cliquez sur le bouton de sélection \(**…**\) situé en regard de la propriété **ImplementedContract**.Dans la fenêtre **Éditeur de collections Type** qui apparaît, cliquez sur la liste déroulante **Type**, et sélectionnez l'entrée **Rechercher des types…**.Dans la boîte de dialogue **Rechercher et sélectionner un type .NET**, sous **\<Projet actif\>**, ouvrez tous les sous\-nœuds et sélectionnez **IBookService**.Cliquez sur **OK**.Dans la boîte de dialogue **Éditeur de collections Type**, cliquez sur **OK**.  
  
6.  Sélectionnez et supprimez les activités **ReceiveRequest** et **SendResponse**.  
  
7.  Dans la boîte à outils, faites glisser **Buy\_ReceiveAndSendReply** et une activité **Checkout\_Receive** sur l'activité **Service séquentiel**.