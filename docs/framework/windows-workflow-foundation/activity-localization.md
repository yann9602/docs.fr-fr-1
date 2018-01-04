---
title: "Localisation d'activité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccabcda9e26751db80ee7e955458d0eee0cae7e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-localization"></a>Localisation d'activité
Lorsque les applications de workflow et les composants ont la possibilité d'être localisés dans d'autres langues et cultures, les chaînes de ressource doivent être utilisées afin qu'ils puissent être localisés sans les recompiler.  
  
## <a name="activity-localization"></a>Localisation d'activité  
 Comme pour les applications devant être localisées (diffusées différentes versions pour diverses langues et cultures), toutes chaînes affichées ne doivent pas être directement encodées, mais plutôt stockées dans un fichier de ressources. Les chaînes peuvent ensuite être accessible via <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`. Si vous développez un composant distribué dans plusieurs langues, vous souhaitez également utiliser des chaînes de ressource pour les messages de validation de l’activité, les données de suivi définies par l’utilisateur, les messages de traçage et les messages d’erreur.  
  
 L'exercice suivant montre comment utiliser un fichier de ressources.  
  
#### <a name="using-resource-files-for-localized-strings"></a>Utilisation de fichiers de ressources pour les chaînes localisées  
  
1.  Dans [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], avec le bouton droit de votre projet dans **l’Explorateur de solutions** et sélectionnez **ajouter...** , **Un nouvel élément...** .  
  
2.  Sélectionnez **fichier de ressources** et nommez le fichier ErrorResources.resx. Cliquez sur **Ajouter**.  
  
3.  Ouvrez le fichier de ressources. Ajouter une nouvelle entrée avec un **nom** d’ErrorString et une **valeur** de « l’activité n’est pas valide. »  
  
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
