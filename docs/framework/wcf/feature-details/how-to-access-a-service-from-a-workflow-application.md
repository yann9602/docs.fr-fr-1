---
title: "Proc&#233;dure&#160;: acc&#233;der &#224; un service &#224; partir d&#39;une application de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Proc&#233;dure&#160;: acc&#233;der &#224; un service &#224; partir d&#39;une application de workflow
Cette rubrique décrit comment appeler un service de workflow à partir d'une application console de workflow.Elle fait suite à la rubrique [Procédure : créer un service de workflow avec les activités de messagerie](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md).Cette rubrique décrit comment appeler un service de workflow à partir d'une application de workflow, mais les mêmes méthodes peuvent être utilisées pour appeler n'importe quel service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] à partir d'une application de workflow.  
  
### Créer un projet d'application console de workflow.  
  
1.  Démarrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Chargez le projet MyWFService que vous avez créé dans la rubrique [Procédure : créer un service de workflow avec les activités de messagerie](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md).  
  
3.  Cliquez avec le bouton droit sur la solution **MyWFService** dans l'**Explorateur de solutions** puis sélectionnez **Ajouter**, **Nouveau projet**.Sélectionnez **Workflow** dans les **Modèles installés** et **Application console de workflow** dans la liste de types de projet.Nommez le projet MyWFClient et utilisez l'emplacement par défaut, comme indiqué dans l'illustration suivante.  
  
     ![Ajouter une nouvelle boîte de dialogue Nouveau projet](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")  
  
     Cliquez sur le bouton **OK** pour fermer la **boîte de dialogue Ajouter un nouveau projet**.  
  
4.  Après avoir créé le projet, le fichier Workflow1.xaml s'ouvre dans le concepteur.Cliquez sur l'onglet **Boîte à outils** pour ouvrir la boîte à outils, si ce n'est pas déjà fait, et cliquez sur la punaise pour garder la fenêtre ouverte.  
  
5.  Appuyez sur CTRL \+ F5 pour générer et lancer le service.Comme auparavant, le Serveur de développement ASP.NET se lance et Internet Explorer affiche la page d'aide WCF.Notez l'URI de cette page, car vous devez l'utiliser dans l'étape suivante.  
  
     ![Internet Explorer affichant la page d'aide et l'URI de WCF](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")  
  
6.  Cliquez avec le bouton droit sur le projet **MyWFClient** dans l'**Explorateur de solutions** et sélectionnez **Ajouter une référence de service**.Cliquez sur le bouton **Découvrir** pour rechercher la solution actuelle pour les services.Cliquez sur le triangle à côté de Service1.xamlx dans la liste des services.Cliquez sur le triangle à côté de Service1 pour répertorier les contrats implémentés par le service Service1.Développez le nœud **Service1** dans la liste des **Services**.L'opération Echo est affichée dans la liste des **Opérations**, comme le montre l'illustration suivante.  
  
     ![Boîte de dialogue Ajouter une référence de service](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")  
  
     Conservez l'espace de noms par défaut et cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une référence de service**.La boîte de dialogue suivante s'affiche.  
  
     ![Boîte de dialogue de notification Ajouter une référence de service](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")  
  
     Cliquez sur **OK** pour fermer la boîte de dialogue.Appuyez ensuite sur Ctrl\+Maj\+B pour générer la solution.Notez qu'une nouvelle section nommée **MyWFClient.ServiceReference1.Activities** a été ajoutée dans la boîte à outils.Développez cette section ; l'activité Echo a été ajoutée comme indiqué dans l'illustration suivante.  
  
     ![Activité Écho dans la boîte à outils](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")  
  
7.  Faites glisser une activité <xref:System.ServiceModel.Activities.Sequence> sur l'aire du concepteur.Elle se trouve sous la section **Flux de contrôle** de la boîte à outils.  
  
8.  Avec l'activité <xref:System.ServiceModel.Activities.Sequence> active, cliquez sur le lien **Variables** et ajoutez une variable de chaîne nommée `inString`.Donnez à la variable la valeur par défaut `« Hello, world »`  ainsi qu'une variable de chaîne nommée `outString`, comme indiqué dans le diagramme suivant.  
  
     ![Ajout d'une variable](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")  
  
9. Faites glisser une activité **Echo** dans l'objet <xref:System.ServiceModel.Activities.Sequence>.Dans la fenêtre des propriétés, liez l'argument \_string à la variable `inString` et l'argument `out_string` à la variable outString, comme indiqué dans l'illustration suivante.Cela transmet la valeur de la variable `inString` à l'opération, puis prend la valeur de retour et la place dans la variable `outString`.  
  
     ![Lier les arguments à des variables](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")  
  
10. Faites glisser une activité **WriteLine** au\-dessous de l'activité **Echo** pour afficher la chaîne retournée par l'appel de service.L'activité **WriteLine** se trouve dans le nœud **Primitives** de la boîte à outils.Liez l'argument **Text** de l'activité **WriteLine** à la variable `outString` en tapant `outString` dans la zone de texte sur l'activité **WriteLine**.Le workflow doit maintenant ressembler à l'illustration suivante.  
  
     ![Flux de travail client complet](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")  
  
11. Cliquez avec le bouton droit sur la solution MyWFService et sélectionnez **Définir les projets de démarrage**Activez la case d'option **Plusieurs projets de démarrage** et sélectionnez **Démarrage** pour chaque projet dans la colonne **Action** comme indiqué dans l'illustration suivante.  
  
     ![Options des projets de démarrage](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")  
  
12. Appuyez sur Ctrl \+ F5 pour lancer à la fois le service et le client.Le Serveur de développement ASP.NET héberge le service, Internet Explorer affiche la page d'aide WCF et l'application de workflow cliente est lancée dans une fenêtre de console et affiche la chaîne retournée par le service \(« Hello, world »\).  
  
## Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [Procédure : créer un service de workflow avec les activités de messagerie](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)   
 [Consommer un service WCF à partir d'un workflow dans un projet Web](http://go.microsoft.com/fwlink/?LinkId=207725)