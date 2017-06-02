---
title: "Proc&#233;dure&#160;: h&#233;berger un service WCF &#233;crit avec le .NET Framework&#160;3.5&#160;dans IIS s&#39;ex&#233;cutant sous le .NET Framework&#160;4 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: h&#233;berger un service WCF &#233;crit avec le .NET Framework&#160;3.5&#160;dans IIS s&#39;ex&#233;cutant sous le .NET Framework&#160;4
Lorsque vous hébergez un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] écrit avec [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] sur un ordinateur qui exécute [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], vous risquez d'obtenir une exception <xref:System.ServiceModel.ProtocolException> avec le texte suivant.  
  
```Output  
Exception non gérée : System.ServiceModel.ProtocolException : le type de contenu text/html; charset=utf-8 du message de réponse ne correspond pas au type de contenu de la liaison (application/soap+xml; charset=utf-8).Lors de l'utilisation d'un encodeur personnalisé, assurez-vous que la méthode IsContentTypeSupported est implémentée correctement.Les 1024 premiers octets de la réponse étaient : '<html>    <head>        <title>Le domaine d'application ou le pool d'applications exécute actuellement la version 4 ou une version ultérieure du .NET Framework.Cela peut se produire si les paramètres IIS ont été définis sur la version 4.0 ou ultérieure pour cette application Web, ou si vous utilisez la version 4.0 ou ultérieure du serveur de développement Web ASP.NET.L'élément <compilation> dans le fichier Web.config de cette application Web ne contient pas l'attribut 'targetFrameworkMoniker' requis pour cette version du .NET Framework (par exemple, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">').Mettez à jour le fichier Web.config avec cet attribut ou configurez l'application Web pour utiliser une version différente du .NET Framework.</title>...  
```  
  
 Si vous essayez également d'accéder au fichier .svc du service, vous risquez d'obtenir une page d'erreur avec le texte suivant.  
  
```Output  
Le domaine d'application ou le pool d'applications exécute actuellement la version 4.0 ou ultérieure du .NET Framework.Cela peut se produire si les paramètres IIS ont été définis sur la version 4.0 ou ultérieure pour cette application Web, ou si vous utilisez la version 4.0 ou ultérieure du serveur de développement Web ASP.NET.L'élément <compilation> dans le fichier Web.config de cette application Web ne contient pas l'attribut 'targetFrameworkMoniker' requis pour cette version du .NET Framework (par exemple, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">').Mettez à jour le fichier Web.config avec cet attribut ou configurez l'application Web pour utiliser une version différente du .NET Framework.  
```  
  
 Ces erreurs se produisent parce que le domaine d'application, dans lequel s'exécute IIS, exécute le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], alors que le service WCF s'attend à fonctionner sous le [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].Cette rubrique explique les modifications nécessaires pour que le service s'exécute.  
  
 Recherchez ensuite l'élément \<`compilers`\> et modifiez l'option de fournisseur CompilerVersion en lui affectant la valeur 4.0.Par défaut, deux éléments \<`compiler`\> se trouvent sous l'élément \<`compilers`\>.Vous devez mettre à jour l'option de fournisseur CompilerVersion pour les deux éléments, comme indiqué dans l'exemple suivant.  
  
```  
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
  
### Ajoutez l'attribut targetFramework nécessaire.  
  
1.  Ouvrez le fichier Web.config du service et recherchez l'élément \<`compilation`\>.  
  
2.  Ajoutez l'attribut `targetFramework` à l'élément \<`compilation`\>, comme indiqué dans l'exemple suivant.  
  
    ```  
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
  
3.  Recherchez l'élément \<`compilers`\> et modifiez l'option de fournisseur CompilerVersion en lui affectant la valeur 4.0.Par défaut, deux éléments \<`compiler`\> se trouvent sous l'élément \<`compilers`\>.Vous devez mettre à jour l'option de fournisseur CompilerVersion pour les deux éléments, comme indiqué dans l'exemple suivant.  
  
    ```  
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