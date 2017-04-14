---
title: "Proc&#233;dure&#160;: cr&#233;er un service de workflow qui appelle un autre service de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Proc&#233;dure&#160;: cr&#233;er un service de workflow qui appelle un autre service de workflow
Il est parfois nécessaire pour un service de workflow d'obtenir des informations d'un autre service de workflow.Cette rubrique montre comment appeler un service de workflow à partir d'un autre service.Dans cette rubrique, vous créerez deux services de workflow ; un qui a une méthode qui inverse la chaîne d'entrée et un autre qui convertit la chaîne d'entrée en majuscules après avoir inversé la chaîne qui utilise le premier service.  
  
### Pour créer le service de workflow Reverser  
  
1.  Exécutez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] en tant qu'administrateur.  
  
2.  Sélectionnez **Fichier**, **Nouveau projet**.Sous le nœud **Workflow** dans le volet **Modèles installés**, sélectionnez **Application de service de workflow WCF**.Nommez la solution `NestedServices`, plus cliquez sur **OK**.  
  
3.  Sous **Serveurs**, assurez\-vous que **Utiliser le serveur Web IIS local** est sélectionné.Cliquez sur **Créer un répertoire virtuel**.Cliquez sur **OK** dans la boîte de dialogue indiquant que le répertoire virtuel a été créé.  
  
4.  Dans l'Explorateur de solutions, renommez Service1.xamlx `StringReverserService.xamlx`.  
  
5.  Sur la page **Propriétés du projet** du nouveau projet, cliquez sur l'onglet **Web**.Définissez l'**Action de démarrage** sur **Page spécifique**, et sélectionnez StringReverserService.xamlx en tant que page de démarrage.  
  
6.  Ouvrez le fichier StringReverserService.xamlx dans le concepteur et supprimez les activités `ReceiveRequest` et `SendReply` existantes, puis faites glisser une activité `ReceiveAndSendReply` dans l'activité de la séquence existante.  
  
    1.  Définissez **OperationName** sur ReverseString.  
  
    2.  Définissez **ServiceContractName** sur IReverseString.  
  
    3.  Activez la case à cocher **CanCreateInstance**.  
  
7.  Sélectionnez l'activité **SequentialService**, puis cliquez sur l'onglet **Variables** en bas du concepteur.Créez deux nouvelles variables nommées StringToReverse et ReversedStringToReturn de type String.  
  
8.  Cliquez sur le lien **Définir** de l'activité **Receive**.Cliquez sur **Paramètres** et créez un paramètre nommé InputString de type String qui assigne à StringToReverse.  
  
9. Cliquez sur le lien **Définir** de l'activité **SendReplyToReceive**.Cliquez sur **Paramètres** et créez un paramètre nommé ReversedString de type String, assigné à ReversedStringToReturn.  
  
10. Pour implémenter la logique pour le service, créez une nouvelle classe nommée StringLibrary dans le projet.Remplacez la définition de la classe par le code suivant.  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
  
    ```  
  
11. Pour appeler la méthode ReverseString sur l'entrée, faites glisser une activité **InvokeMethod** de la boîte à outils vers l'espace situé entre les activités **Receive** et **SendReply**.Définissez les propriétés de l'activité comme ci\-dessous.  
  
    1.  **MethodName** : ReverseString  
  
    2.  **Result** : ReversedStringToReturn  
  
    3.  **Paramètres** : créez un paramètre avec une **Direction** In, un **Type** String et une **Valeur** StringToReverse.  
  
    4.  **TargetType** : NestedServices.StringLibrary  
  
12. Testez le service en appuyant sur F5.Dans le Client test WCF qui s'affiche, double\-cliquez sur la méthode ReverseString\(\).Dans le volet Requête, entrez `Sample` pour la valeur du paramètre InputString.Cliquez sur **Appeler**.Le service doit retourner « elpmaS ».  
  
### Pour créer le service de workflow UpperCaser  
  
1.  Cliquez avec le bouton droit sur le projet NestedServices et sélectionnez **Ajouter**, **Nouvel élément**.Sous le nœud **Workflow**, sélectionnez **Service de workflow WCF**, et nommez le nouveau service `UpperCaserService`.Cliquez sur **Ajouter**.Un nouveau service de workflow nommé UpperCaserService.xamlx doit être ajouté au projet.  
  
2.  Ouvrez le fichier UpperCaserServices.xamlx dans le concepteur et supprimez les activités **ReceiveRequest** et `SendReply` existantes, puis faites glisser une activité `ReceiveAndSendReply` dans l'activité de la séquence existante.  
  
    1.  Définissez **OperationName** sur UpperCaseString.  
  
    2.  Définissez **ServiceContractName** sur IUpperCaseString.  
  
    3.  Activez la case à cocher **CanCreateInstance**.  
  
3.  Sélectionnez l'activité SequentialService, puis cliquez sur l'onglet **Variables** en bas du concepteur.Créez trois nouvelles variables nommées StringToUpper, StringToReverse et StringToReturn de type String.  
  
4.  Cliquez sur le lien **Définir** de l'activité **Receive**.Cliquez sur **Paramètres** et créez un paramètre nommé InputString de type String qui assigne à StringToUpper.  
  
5.  Cliquez sur le lien **Définir** de l'activité **SendReplyToReceive**.Cliquez sur **Paramètres** et créez un paramètre nommé ModifiedString de type String, assigné à StringToReturn.  
  
6.  Pour implémenter la logique pour le service, créez une nouvelle méthode dans la classe StringLibrary à l'aide du code suivant.  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
  
    ```  
  
7.  Pour appeler la méthode UpperCaseString sur l'entrée, faites glisser une activité **InvokeMethod** de la boîte à outils vers l'espace situé entre les activités **Receive** et **SendReply**.Définissez les propriétés de l'activité comme ci\-dessous.  
  
    1.  **MethodName** : UpperCaseString  
  
    2.  **Result** : StringToReverse  
  
    3.  **Paramètres** : créez un paramètre avec une **Direction** In, un **Type** String et une **Valeur** StringToUpper.  
  
    4.  **TargetType** : NestedServices.StringLibrary  
  
8.  Vous allez maintenant appeler le premier service sur la chaîne modifiée.Cliquez avec le bouton droit sur le projet et sélectionnez **Ajouter une référence de service**.Ajoutez une référence de service à http:\/\/localhost\/NestedServices\/StringReverserService.xamlx et générez le projet pour créer une activité personnalisée permettant d'accéder au premier service Web.  
  
9. Faites glisser une instance de la nouvelle activité sur le workflow, entre l'activité **InvokeMethod** et les activités **SendReplyToReceive**.Assignez la variable StringToReverse à la propriété InputString de la nouvelle activité, et la variable StringToReturn à la propriété StringToReturn.  
  
10. Ouvrez la page Propriétés pour le projet NestedServices, et remplacez la **Page spécifique** dans l'onglet **Web** par UpperCaserService.xamlx.  
  
11. Testez le service en appuyant sur F5.Dans le Client test WCF qui s'affiche, double\-cliquez sur la méthode ReverseString\(\).Dans le volet Requête, entrez `Sample` pour la valeur du paramètre InputString.Cliquez sur **Appeler**.Le service doit retourner « ELPMAS ».  
  
### Pour créer un client qui appelle les services  
  
1.  Ajoutez à la solution un nouveau projet d'application console nommé Client.  
  
2.  Cliquez avec le bouton droit sur le projet Client et sélectionnez **Ajouter une référence de service**.Dans la fenêtre qui s'affiche, cliquez sur **Découvrir**.Sélectionnez StringReverserService.xamlx et entrez ReverseService comme espace de noms.Cliquez sur **OK**.  
  
3.  Remplacez le code de la méthode Main dans Program.cs par le code suivant.  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
  
    ```