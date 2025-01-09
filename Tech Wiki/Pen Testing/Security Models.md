Tags: [[Penetration Testing]] [[Cybersecurity]] [[Tags/Security Models]] #Pentesting #SecurityModels

The **Bell-La Padula Model** is used to achieve confidentiality. This model has a few assumptions, such as an organization's hierarchical structure it is used in, where everyone's responsibilities/roles are well-defined.

The model works by granting access to pieces of data (called objects) on a strictly need to know basis. This model uses the rule "no write down, no read up".


![[Screenshot 2024-11-28 095312.png]]


![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/0e6e5d9d80785fc287b4a67e1453b295.png)

## Biba Model
The Biba model is arguably the equivalent of the Bell-La Padula model but for the integrity of the CIA triad.

  

This model applies the rule to objects (data) and subjects (users) that can be summarised as "no write up, no read down". This rule means that subjects **can** create or write content to objects at or below their level but **can only** read the contents of objects above the subject's level.

  

Let's compare some advantages and disadvantages of this model in the table below:

![[Screenshot 2024-11-28 095805.png]]


![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5de96d9ca744773ea7ef8c00/room-content/895ba351ef24ef6495d290222e49470e.png)
