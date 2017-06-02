---
title: "Proc&#233;dure&#160;: cr&#233;er un service qui retourne des donn&#233;es arbitraires &#224; l&#39;aide du mod&#232;le de programmation Web HTTP WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Proc&#233;dure&#160;: cr&#233;er un service qui retourne des donn&#233;es arbitraires &#224; l&#39;aide du mod&#232;le de programmation Web HTTP WCF
Les développeurs doivent parfois avoir le contrôle total de la manière dont les données sont retournées à partir d'une opération de service.C'est le cas lorsqu'une opération de service doit retourner des données dans un format non pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Cette rubrique décrit l'utilisation du modèle de programmation Web HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour créer un tel service.Ce service a une opération qui retourne un flux de données.  
  
### Pour implémenter le contrat de service  
  
1.  Définition du contrat de service.Le contrat est appelé `IImageServer` et a une méthode appelée `GetImage` qui retourne un <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     La méthode retournant un <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suppose que l'opération a un contrôle complet sur les octets retournés à partir de l'opération de service et elle n'applique aucune mise en forme aux données retournées.  
  
2.  Implémentez le contrat de service.Le contrat a une seule opération \(`GetImage`\).Cette méthode génère une image bitmap, puis l'enregistre dans un <xref:System.IO.MemoryStream> au format .jpg.L'opération retourne ensuite ce flux de données à l'appelant.  
  
    ```  
    public class Service : IImageServer  
       {  
           public Stream GetImage(int width, int height)  
           {  
               Bitmap bitmap = new Bitmap(width, height);  
               for (int i = 0; i < bitmap.Width; i++)  
               {  
                   for (int j = 0; j < bitmap.Height; j++)  
                   {  
                       bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                   }  
               }  
               MemoryStream ms = new MemoryStream();  
               bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
               ms.Position = 0;  
               WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
               return ms;  
           }  
       }  
    ```  
  
     Observez l'avant\-dernière ligne de code : `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Elle affecte à l'en\-tête de type de contenu la valeur `“image/jpeg”`.Bien que cet exemple indique comment retourner un fichier .jpg, il peut être modifié pour retourner tout type de données requis, dans n'importe quel format.L'opération doit extraire ou générer les données, puis les écrire dans un flux de données.  
  
### Pour héberger le service  
  
1.  Créez une application console pour héberger le service.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  Créez une variable pour stocker l'adresse de base du service dans la méthode `Main`.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Créez une instance <xref:System.ServiceModel.ServiceHost> pour le service spécifiant son adresse de base et sa classe.  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
  
    ```  
  
4.  Ajoutez un point de terminaison à l'aide de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
  
    ```  
  
5.  Ouvrir l'hôte de service.  
  
    ```  
    host.Open()  
    ```  
  
6.  Patientez jusqu'à ce que l'utilisateur appuie sur ENTRÉE pour arrêter le service.  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
  
    ```  
  
### Pour appeler le service brut à l'aide d'Internet Explorer  
  
1.  Exécutez le service. La sortie suivante devrait apparaître.`Service is running Press ENTER to close the host`  
  
2.  Ouvrez Internet Explorer et tapez `http://localhost:8000/Service/GetImage?width=50&height=40`. Un rectangle jaune traversé en son centre par une ligne diagonale bleue devrait apparaître.  
  
## Exemple  
 L'intégralité du code utilisé dans cette rubrique est présentée ci\-dessous.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
  
```  
  
## Compilation du code  
  
-   Lors de la compilation de l'exemple de code, faites référence à System.ServiceModel.dll et System.ServiceModel.Web.dll.  
  
## Voir aussi  
 [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)