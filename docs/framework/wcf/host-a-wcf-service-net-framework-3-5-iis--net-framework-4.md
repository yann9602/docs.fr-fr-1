---
title: "Procédure : héberger un service WCF écrit avec le .NET Framework 3.5 dans IIS s'exécutant sous le .NET Framework 4"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81aa47747d27f135c270959f2c8abf03c522bf87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a>Procédure : héberger un service WCF écrit avec le .NET Framework 3.5 dans IIS s'exécutant sous le .NET Framework 4
Lorsque vous hébergez un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] écrit avec [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] sur un ordinateur qui exécute [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], vous risquez d'obtenir une exception <xref:System.ServiceModel.ProtocolException> avec le texte suivant.  
  
```Output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 Si vous essayez également d'accéder au fichier .svc du service, vous risquez d'obtenir une page d'erreur avec le texte suivant.  
  
```Output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 Ces erreurs se produisent parce que le domaine d'application, dans lequel s'exécute IIS, exécute le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], alors que le service WCF s'attend à fonctionner sous le [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Cette rubrique explique les modifications nécessaires pour que le service s'exécute.  
  
 Recherchez ensuite le <`compilers`> élément et modifiez l’option de fournisseur CompilerVersion pour avoir la valeur 4.0. Par défaut, il y a deux <`compiler`> éléments sous le <`compilers`> élément. Vous devez mettre à jour l'option de fournisseur CompilerVersion pour les deux éléments, comme indiqué dans l'exemple suivant.  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a>Ajoutez l'attribut targetFramework nécessaire.  
  
1.  Ouvrez le fichier du service Web.config et recherchez la <`compilation`> élément.  
  
2.  Ajouter le `targetFramework` d’attribut pour le <`compilation`> élément, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3.  Rechercher le <`compilers`> élément et modifiez l’option de fournisseur CompilerVersion pour avoir la valeur 4.0. Par défaut, il y a deux <`compiler`> éléments sous le <`compilers`> élément. Vous devez mettre à jour l'option de fournisseur CompilerVersion pour les deux éléments, comme indiqué dans l'exemple suivant.  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
