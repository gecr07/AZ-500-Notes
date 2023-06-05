# AZ-500-Notes

## Explore Azure Active Directory features

> Azure Active Directory (Azure AD) is a cloud-based identity and access management service. This service helps employees access external resources, such as Microsoft 365, the Azure portal, and thousands of other software-as-a-service (SaaS) applications. Azure Active Directory also helps them access internal resources like apps on your corporate intranet network, along with any cloud apps developed for your organization.


## What are the Azure AD licenses?

![image](https://github.com/gecr07/AZ-500-Notes/assets/63270579/23ebde66-b85f-42f0-b62f-92e6fa1b222a)

Although the three Active Directory-based identity solutions share a common name and technology, they're designed to provide services that meet different customer demands. At a high level, these identity solutions and feature sets are:



## Self-managed Active Directory Domain Services



## Azure Active Directory (Azure AD )

Azure Active Directory (Azure AD) - Cloud-based identity and mobile device management that provides user account and authentication services for resources such as Microsoft 365, the Azure portal, or SaaS applications.
Azure AD can be synchronized with an on-premises AD DS environment to provide a single identity to users that works natively in the cloud.


## Managed Azure Active Directory Domain Services



## Active Directory Domain Services (AD DS) 

Enterprise-ready lightweight directory access protocol (LDAP) server that provides key features such as identity and authentication, computer object management, group policy, and trusts.
AD DS is a central component in many organizations with an on-premises IT environment and provides core user account authentication and computer management features

## Azure Active Directory Domain Services (Azure AD DS) 

Provides managed domain services with a subset of fully compatible traditional AD DS features such as domain join, group policy, LDAP, and Kerberos / New Technology LAN Manager (NTLM) authentication.
Azure AD DS integrates with Azure AD, which can synchronize with an on-premises AD DS environment. This ability extends central identity use cases to traditional web applications that run in Azure as part of a lift-and-shift strategy.

### Azure AD DS and self-managed AD DS

If you have applications and services that need access to traditional authentication mechanisms such as Kerberos or NTLM, there are two ways to provide Active Directory Domain Services in the cloud:

-A managed domain that you create using Azure Active Directory Domain Services (Azure AD DS). Microsoft creates and manages the required resources.

-A self-managed domain that you create and configure using traditional resources such as virtual machines (VMs), Windows Server guest OS, and Active Directory Domain Services (AD DS). You then continue to administer these resources.


Los modelos de implementación comunes para un entorno de AD DS autoadministrado que proporciona identidad a las aplicaciones y servicios en la nube incluyen los siguientes:


Standalone cloud-only AD DS - Azure VMs are configured as domain controllers, and a separate, cloud-only AD DS environment is created. This AD DS environment doesn't integrate with an on-premises AD DS environment. A different set of credentials is used to sign in and administer VMs in the cloud.

Resource forest deployment - Azure VMs are configured as domain controllers, and an AD DS domain that's part of an existing forest is created. A trust relationship is then configured to an on-premises AD DS environment. Other Azure VMs can domain-join this resource forest in the cloud. User authentication runs over a VPN / ExpressRoute connection to the on-premises AD DS environment.

Extend on-premises domain to Azure - An Azure virtual network connects to an on-premises network using a VPN / ExpressRoute connection. Azure VMs connect to this Azure virtual network, which lets them domain-join to the on-premises AD DS environment.

An alternative is to create Azure VMs and promote them as replica domain controllers from the on-premises AD DS domain. These domain controllers replicate over a VPN / ExpressRoute connection to the on-premises AD DS environment. The on-premises AD DS domain is effectively extended into Azure.





















