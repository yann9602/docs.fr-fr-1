---
title: "How to: Configure .NET Framework-Based COM Components for Registration-Free Activation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "components [.NET Framework], manifest"
  - "application manifests [.NET Framework]"
  - "manifests [.NET Framework]"
  - "registration-free COM interop, configuring .NET-based components"
  - "activation, registration-free"
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Configure .NET Framework-Based COM Components for Registration-Free Activation
L'activation sans inscription des composants .NET Framework n'est que légèrement plus compliquée que pour les composants COM.  L'installation requiert deux manifestes :  
  
-   Les applications COM doivent avoir un manifeste d'application de style Win32 pour identifier le composant managé.  
  
-   Les composants .NET Framework doivent avoir un manifeste de composant pour les informations d'activation nécessaires au moment de l'exécution.  
  
 Cette rubrique explique comment associer un manifeste d'application à une application, comment associer un manifeste de composant à un composant et comment incorporer un manifeste de composant dans un assembly.  
  
### Pour créer un manifeste d'application  
  
1.  À l'aide d'un éditeur XML, créez \(ou modifiez\) le manifeste d'application de l'application COM qui interagit avec un ou plusieurs composants managés.  
  
2.  Insérez l'en\-tête standard suivant au début du fichier :  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     Pour plus d'informations sur les éléments de manifeste et leurs attributs, recherchez « Application Manifests Reference » dans MSDN Library.  
  
3.  Identifiez le propriétaire du manifeste.  Dans l'exemple suivant, le fichier de manifeste appartient à `myComApp` version 1.  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  Identifiez les assemblys dépendants.  Dans l'exemple suivant, `myComApp` dépend de `myManagedComp`.  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  Nommez et enregistrez le fichier de manifeste.  Le nom d'un manifeste d'application est le nom de l'assembly exécutable suivi de l'extension .manifest.  Par exemple, le nom du fichier de manifeste d'application de myComApp.exe est myComApp.exe.manifest.  
  
 Vous pouvez installer un manifeste d'application dans le même répertoire que l'application COM.  Vous pouvez également l'ajouter en tant que ressource au fichier .exe de l'application.  Pour plus d'informations, recherchez « Side\-by\-side Assemblies » dans MSDN Library.  
  
#### Pour créer un manifeste de composant  
  
1.  À l'aide d'un éditeur XML, créez un manifeste de composant pour décrire l'assembly managé.  
  
2.  Insérez l'en\-tête standard suivant au début du fichier :  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  Identifiez le propriétaire du manifeste.  L'élément `<assemblyIdentity>` de l'élément `<dependentAssembly>` dans le fichier de manifeste d'application doit correspondre à celui figurant dans le manifeste de composant.  Dans l'exemple suivant, le fichier de manifeste appartient à `myManagedComp` version 1.2.3.4.  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  Identifiez chaque classe dans l'assembly.  Utilisez l'élément `<clrClass>` pour identifier de manière unique chaque classe dans l'assembly managé.  L'élément, qui est un sous\-élément de l'élément `<assembly>`, a les attributs décrits dans le tableau suivant.  
  
    |Attribut|Description|Obligatoire|  
    |--------------|-----------------|-----------------|  
    |`clsid`|Identificateur qui spécifie la classe à activer.|Oui|  
    |`description`|Chaîne qui informe l'utilisateur sur le composant.  L'attribut par défaut est une chaîne vide.|Non|  
    |`name`|Chaîne représentant la classe managée.|Oui|  
    |`progid`|Identificateur à utiliser pour une activation à liaison tardive.|Non|  
    |`threadingModel`|Modèle de thread COM. "Both" est la valeur par défaut.|Non|  
    |`runtimeVersion`|Spécifie la version du common language runtime \(CLR\) à utiliser.  Si vous ne spécifiez pas cet attribut et si le CLR n'est pas déjà chargé, le composant est chargé avec la version du CLR la plus récente, antérieure à la version CLR 4.  Si vous spécifiez v1.0.3705, v1.1.4322 ou v2.0.50727, la version passe automatiquement à la version du CLR installée la plus récente antérieure à la version CLR 4 \(habituellement v2.0.50727\).  Si une autre version du CLR est déjà chargée, et si la version spécifiée peut être chargée in\-process côte à côte, la version spécifiée est chargée ; sinon, le CLR chargé est utilisé.  Cela peut provoquer un échec de chargement.|Non|  
    |`tlbid`|Identificateur de la bibliothèque de types qui contient les informations de type sur la classe.|Non|  
  
     Toutes les balises d'attribut respectent la casse.  Vous pouvez obtenir des CLSID, des ProgID, des modèles de thread et la version du runtime en affichant la bibliothèque de types exportée de l'assembly à l'aide de l'explorateur d'objets OLE\/COM \(Oleview.exe\).  
  
     Le manifeste de composant suivant identifie deux classes, `testClass1` et `testClass2`.  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4" />  
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  Nommez et enregistrez le fichier de manifeste.  Le nom d'un manifeste de composant est le nom de la bibliothèque d'assembly suivi de l'extension .manifest.  Par exemple, le nom du fichier de manifeste de composant de myManagedComp.dll est myManagedComp.manifest.  
  
 Vous devez incorporer le manifeste de composant en tant que ressource dans l'assembly.  
  
#### Pour incorporer un manifeste de composant dans un assembly managé  
  
1.  Créez un script de ressources qui contient l'instruction suivante :  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     Dans cette instruction, `myManagedComp.manifest` est le nom du manifeste de composant incorporé.  Pour cet exemple, le nom du fichier de script est `myresource.rc`.  
  
2.  Compilez le script à l'aide du compilateur de ressources Microsoft Windows \(Rc.exe\).  À l'invite de commandes, tapez la commande suivante :  
  
     `rc myresource.rc`  
  
     Rc.exe génère le fichier de ressources `myresource.res`.  
  
3.  Compilez de nouveau le fichier source de l'assembly et spécifiez le fichier de ressources à l'aide de l'option **\/win32res** :  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     `myresource.res` est de nouveau le nom du fichier de ressources contenant la ressource incorporée.  
  
## Voir aussi  
 [Registration\-Free COM Interop](../../../docs/framework/interop/registration-free-com-interop.md)   
 [Requirements for Registration\-Free COM Interop](http://msdn.microsoft.com/fr-fr/0c43bc57-eecf-4e6c-8114-490141cce4da)   
 [Configuring COM Components for Registration\-Free Activation](http://msdn.microsoft.com/fr-fr/bfe9b02f-d964-4784-960e-a1f94692fbfe)   
 [Registration\-Free Activation of .NET\-Based Components: A Walkthrough](http://go.microsoft.com/fwlink/?LinkId=158812)