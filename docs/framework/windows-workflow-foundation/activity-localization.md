---
title: "Localisation d&#39;activit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Localisation d&#39;activit&#233;
Lorsque les applications de workflow et les composants ont la possibilité d'être localisés dans d'autres langues et cultures, les chaînes de ressource doivent être utilisées afin qu'ils puissent être localisés sans les recompiler.  
  
## Localisation d'activité  
 Comme pour les applications devant être localisées \(diffusées différentes versions pour diverses langues et cultures\), toutes chaînes affichées ne doivent pas être directement encodées, mais plutôt stockées dans un fichier de ressources.Ils sont alors accessibles par <xref:System.Environment.GetResourceString>.Si vous développez un composant distribué dans plusieurs langues, vous souhaitez également utiliser des chaînes de ressource pour les messages de validation de l'activité, les données de suivi définies par l'utilisateur, les messages de traçage et les messages d'erreur.  
  
 L'exercice suivant montre comment utiliser un fichier de ressources.  
  
#### Utilisation de fichiers de ressources pour les chaînes localisées  
  
1.  Dans [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], cliquez avec le bouton droit sur votre projet dans l'**Explorateur de solutions**, puis sélectionnez **Ajouter**, **Nouvel élément**.  
  
2.  Sélectionnez **Fichier de ressources** et nommez le fichier ErrorResources.resx.Cliquez sur **Ajouter**.  
  
3.  Ouvrez le fichier de ressources.Ajoutez une nouvelle entrée avec un **Nom** d'ErrorString et une **Valeur** de « L'activité n'est pas valide ».  
  
4.  Ajoutez les instructions `using` suivantes à votre classe.  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
  
    ```  
  
5.  Créez un gestionnaire de ressources dans votre projet.  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
  
    ```  
  
6.  Obtenez la chaîne du gestionnaire de ressources où c'est obligatoire.  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
  
    ```  
  
 L'exemple de code suivant montre comment utiliser des chaînes localisées dans la méthode <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```