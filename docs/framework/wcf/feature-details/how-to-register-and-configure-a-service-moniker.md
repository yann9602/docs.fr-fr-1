---
title: "Comment : inscrire et configurer un moniker de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 86938301d28cbb0293ece4b3e12a2ef2d2a54e69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-and-configure-a-service-moniker"></a>Comment : inscrire et configurer un moniker de service
Avant d'utiliser le moniker de service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans une application COM avec un contrat typé, vous devez inscrire les types avec attributs requis avec COM et paramétrer l'application COM et le moniker avec la configuration de liaison requise.  
  
### <a name="to-register-the-required-attributed-types-with-com"></a>Pour inscrire les types avec attributs requis avec COM  
  
1.  Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil pour récupérer le contrat de métadonnées à partir de la [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service. Cette opération génère le code source d'un assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et un fichier de configuration d'application cliente.  
  
2.  Vérifiez que les types dans l'assembly sont marqués comme `ComVisible`. Pour cela, ajoutez l'attribut suivant au fichier AssemblyInfo.cs dans votre projet Visual Studio.  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  Compilez le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] managé comme un assembly avec nom fort. Cette procédure requiert une signature à l'aide d'une paire de clés de chiffrement. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Signature d’un Assembly avec un nom fort](http://go.microsoft.com/fwlink/?LinkId=94874) dans le Guide du développeur .NET.  
  
4.  Utilisez l'outil Assembly Registration Tool (Regasm.exe) avec l'option `/tlb` pour inscrire les types dans l'assembly avec COM.  
  
5.  Utilisez l'outil Global Assembly Cache Tool (Gacutil.exe) pour ajouter l'assembly au Global Assembly Cache.  
  
    > [!NOTE]
    >  La signature de l'assembly et son ajout au Global Assembly Cache sont deux étapes facultatives, mais elles peuvent simplifier le processus de chargement de l'assembly à partir de l'emplacement approprié au moment de l'exécution.  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a>Pour configurer l’application COM et le moniker à l’aide des paramètres de liaison requis  
  
-   Placez les définitions de liaison (généré par le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dans le fichier de configuration d’application client généré) dans le fichier de configuration de l’application cliente. Par exemple, pour un fichier exécutable Visual Basic 6.0 nommé CallCenterClient.exe, la configuration doit être placée dans un fichier nommé CallCenterConfig.exe.config, dans le même répertoire que le fichier exécutable. L'application cliente peut maintenant utiliser le moniker. Notez que la configuration de liaison n'est pas requise si vous utilisez l'un des types de liaison standard fournis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
     Le type suivant est inscrit.  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     L'application est exposée à l'aide d'une liaison `wsHttpBinding`. Pour une configuration de type et d'application donnée, les exemples de chaînes de moniker suivants sont utilisés.  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     Vous pouvez utiliser l'une ou l'autre de ces chaînes de moniker à partir de l'application Visual Basic 6.0, après avoir ajouté une référence à l'assembly qui contient les types `IMathService`, tel qu'indiqué dans l'exemple de code suivant.  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     Dans cet exemple, la définition de la configuration de liaison `Binding1` est stockée dans un fichier de configuration judicieusement nommé pour l'application cliente, par exemple vb6nomapp.exe.config.  
  
    > [!NOTE]
    >  Vous pouvez utiliser un code semblable dans une application C#, C++ ou d'un autre langage .NET.  
  
    > [!NOTE]
    >  Si le moniker est incorrect ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur de type « Syntaxe non valide ». Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
     Bien que cette rubrique porte sur l'utilisation du moniker de service à partir du code VB 6.0, vous pouvez utiliser un moniker de service à partir d'autres langages. Lors de l'utilisation d'un moniker à partir du code C++, l'assembly généré par Svcutil.exe doit être importé avec le paramètre « no_namespace named_guids raw_interfaces_only », tel qu'indiqué dans le code suivant.  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     Cela modifie les définitions d'interface importées afin que toutes les méthodes retournent un `HResult`. Toutes les autres valeurs de retour sont converties en paramètres de sortie. L'exécution globale des méthodes reste la même. Cela vous permet de déterminer la cause d'une exception lorsque vous appelez une méthode sur le proxy. Cette fonctionnalité n'est disponible qu'à partir du code C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
