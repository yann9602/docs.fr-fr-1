---
title: "Guide pratique pour configurer le suivi réseau"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
caps.latest.revision: "23"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 12f328d58ef568c78d1e2c8a8ff564839cba9f3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="5e94b-102">Guide pratique pour configurer le suivi réseau</span><span class="sxs-lookup"><span data-stu-id="5e94b-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="5e94b-103">Le fichier de configuration de l'application ou de l'ordinateur contient les paramètres qui déterminent le format et le contenu des traces réseau.</span><span class="sxs-lookup"><span data-stu-id="5e94b-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="5e94b-104">Avant d'effectuer cette procédure, assurez-vous que le traçage est activé.</span><span class="sxs-lookup"><span data-stu-id="5e94b-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="5e94b-105">Pour plus d’informations sur l’activation du suivi, consultez [Activation du suivi réseau](../../../docs/framework/network-programming/enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="5e94b-105">For information about enabling tracing, see [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="5e94b-106">Le fichier de configuration de l’ordinateur, machine.config, est stocké dans le dossier %Windir%\Microsoft.NET\Framework dans le répertoire dans lequel Windows a été installé.</span><span class="sxs-lookup"><span data-stu-id="5e94b-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="5e94b-107">Il est un fichier machine.config distinct dans les dossiers sous %Windir%\Microsoft.NET\Framework pour chaque version du .NET Framework sont installées sur l’ordinateur (par exemple, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config ou C:\Windows\ Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="5e94b-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="5e94b-108">Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5e94b-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="5e94b-109">Pour configurer le traçage réseau</span><span class="sxs-lookup"><span data-stu-id="5e94b-109">To configure network tracing</span></span>  
  
-   <span data-ttu-id="5e94b-110">Ajoutez les lignes suivantes au fichier de configuration approprié.</span><span class="sxs-lookup"><span data-stu-id="5e94b-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="5e94b-111">Les valeurs et les options de ces paramètres sont décrites dans les tableaux ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5e94b-111">The values and options for these settings are described in the tables below.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="System.Net" tracemode="includehex" maxdatasize="1024">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Cache">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Http">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Sockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.WebSockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="System.Net" value="Verbose"/>  
          <add name="System.Net.Cache" value="Verbose"/>  
          <add name="System.Net.Http" value="Verbose"/>  
          <add name="System.Net.Sockets" value="Verbose"/>  
          <add name="System.Net.WebSockets" value="Verbose"/>  
        </switches>  
        <sharedListeners>  
          <add name="System.Net"  
            type="System.Diagnostics.TextWriterTraceListener"  
            initializeData="network.log"  
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 <span data-ttu-id="5e94b-112">Lorsque vous ajoutez un nom au bloc `<switches>`, la sortie de trace inclut les informations de certaines méthodes associées au nom.</span><span class="sxs-lookup"><span data-stu-id="5e94b-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="5e94b-113">Le tableau suivant décrit la sortie.</span><span class="sxs-lookup"><span data-stu-id="5e94b-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="5e94b-114">Nom</span><span class="sxs-lookup"><span data-stu-id="5e94b-114">Name</span></span>|<span data-ttu-id="5e94b-115">Sortie de</span><span class="sxs-lookup"><span data-stu-id="5e94b-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="5e94b-116">Certaines méthodes publiques des classes <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient> et <xref:System.Net.Dns></span><span class="sxs-lookup"><span data-stu-id="5e94b-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="5e94b-117">Certaines méthodes publiques des classes <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse>, et les informations de débogage de SSL (les certificats non valides, la liste des émetteurs manquants et les erreurs de certificat client.)</span><span class="sxs-lookup"><span data-stu-id="5e94b-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="5e94b-118">Certaines méthodes publiques des classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> et <xref:System.Net.HttpListenerResponse>.</span><span class="sxs-lookup"><span data-stu-id="5e94b-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="5e94b-119">Certaines méthodes privées et internes dans `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="5e94b-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="5e94b-120">Certaines méthodes publiques des classes <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> et <xref:System.Net.Http.WebRequestHandler>.</span><span class="sxs-lookup"><span data-stu-id="5e94b-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="5e94b-121">Certaines méthodes publiques des classes <xref:System.Net.WebSockets.ClientWebSocket> et <xref:System.Net.WebSockets.WebSocket>.</span><span class="sxs-lookup"><span data-stu-id="5e94b-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="5e94b-122">Les attributs répertoriés dans le tableau suivant configurent la sortie de trace.</span><span class="sxs-lookup"><span data-stu-id="5e94b-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="5e94b-123">Nom d'attribut</span><span class="sxs-lookup"><span data-stu-id="5e94b-123">Attribute name</span></span>|<span data-ttu-id="5e94b-124">Valeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="5e94b-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="5e94b-125">Attribut <xref:System.String> requis.</span><span class="sxs-lookup"><span data-stu-id="5e94b-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="5e94b-126">Définit les commentaires de la sortie.</span><span class="sxs-lookup"><span data-stu-id="5e94b-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="5e94b-127">Les valeurs légitimes sont `Critical`, `Error`, `Verbose`, `Warning` et `Information`.</span><span class="sxs-lookup"><span data-stu-id="5e94b-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="5e94b-128">Cet attribut doit être défini sur l’élément \<add name> de l’élément \<switches> comme illustré dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="5e94b-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="5e94b-129">Une exception est levée si cet attribut est défini sur l’élément \<source>.</span><span class="sxs-lookup"><span data-stu-id="5e94b-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="5e94b-130">Attribut <xref:System.Int32> facultatif.</span><span class="sxs-lookup"><span data-stu-id="5e94b-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="5e94b-131">Définit le nombre maximal d'octets de données réseau incluses dans chaque trace de ligne.</span><span class="sxs-lookup"><span data-stu-id="5e94b-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="5e94b-132">La valeur par défaut est 1024.</span><span class="sxs-lookup"><span data-stu-id="5e94b-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="5e94b-133">Cet attribut doit être défini sur l’élément \<source> comme illustré dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="5e94b-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="5e94b-134">Une exception est levée si cet attribut est défini sur un élément sous l’élément \<switches>.</span><span class="sxs-lookup"><span data-stu-id="5e94b-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="5e94b-135">Attribut <xref:System.String> facultatif.</span><span class="sxs-lookup"><span data-stu-id="5e94b-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="5e94b-136">Définissez la valeur `includehex` pour afficher les traces de protocole au format hexadécimal et texte.</span><span class="sxs-lookup"><span data-stu-id="5e94b-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="5e94b-137">Définissez la valeur `protocolonly` pour afficher uniquement du texte.</span><span class="sxs-lookup"><span data-stu-id="5e94b-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="5e94b-138">La valeur par défaut est `includehex`.</span><span class="sxs-lookup"><span data-stu-id="5e94b-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="5e94b-139">Cet attribut doit être défini sur l’élément \<switches> comme illustré dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="5e94b-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="5e94b-140">Une exception est levée si cet attribut est défini sur un élément sous l’élément \<source>.</span><span class="sxs-lookup"><span data-stu-id="5e94b-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e94b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e94b-141">See Also</span></span>  
 [<span data-ttu-id="5e94b-142">Interprétation du traçage réseau</span><span class="sxs-lookup"><span data-stu-id="5e94b-142">Interpreting Network Tracing</span></span>](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [<span data-ttu-id="5e94b-143">Traçage réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5e94b-143">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 [<span data-ttu-id="5e94b-144">L’activation du traçage réseau</span><span class="sxs-lookup"><span data-stu-id="5e94b-144">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [<span data-ttu-id="5e94b-145">Introduction à l’instrumentation et au traçage</span><span class="sxs-lookup"><span data-stu-id="5e94b-145">Introduction to Instrumentation and Tracing</span></span>](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
