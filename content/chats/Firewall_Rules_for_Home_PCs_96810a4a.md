---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Firewall Rules for Home PCs

Created: 2024-07-26 01:27:55 UTC
Updated: 2024-07-26 01:28:09 UTC
UUID: 96810a4a-1221-4c84-838e-e82fddec0fe9
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-07-26 01:28:06 UTC

id like to you give me some input on a question i have about firewall rules, aliases, to be specific. 

i have 2 pcs that i use in my home. if i want them to have free access to my home network, can i make a PCs alias, include their ip addresses in the alias and then drop the alias into rules on all of the vlans i want them to have access to? what about communication between these devices? they're both windows pcs, so having sharing working as expected would be nice, even with them on different vlans.

---

**Assistant** - 2024-07-26 01:28:06 UTC

 Your approach of using an alias for your PCs is a good starting point for managing firewall rules. Let's break down your question and consider the implications:

1. Creating a PCs alias:
   Yes, you can create an alias that includes the IP addresses of both PCs. This is an efficient way to manage rules for multiple devices.

2. Using the alias in firewall rules:
   You can indeed use this alias in firewall rules across different VLANs to grant access. This would allow both PCs to access resources on those VLANs.

3. Communication between devices:
   If the PCs are on different VLANs, you'll need to consider a few additional points:

   a. Inter-VLAN routing: Ensure your router/firewall is configured to route traffic between the VLANs where your PCs are located.

   b. Firewall rules: You'll need rules that explicitly allow traffic between these two PCs. This could be done by creating rules that allow traffic:
      - From PC1's IP to PC2's IP (and vice versa)
      - From the PCs alias to itself

   c. Windows file sharing: For Windows file sharing (SMB) to work across VLANs, you'll need to ensure that the following ports are open between the PCs:
      - TCP 445 (SMB)
      - TCP 135, 137-139 (NetBIOS)

4. Security considerations:
   While this setup can work, be mindful of the security implications. Granting broad access across multiple VLANs may potentially expose your PCs to more risk. Consider implementing additional security measures like:
   - Using strong authentication methods
   - Keeping your PCs updated and running antivirus software
   - Monitoring and logging inter-VLAN traffic

5. Alternative approach:
   Depending on your network setup and requirements, you might consider placing both PCs on the same VLAN if they need frequent communication and file sharing. This could simplify your firewall rules and potentially improve performance for local file sharing.

Would you like me to elaborate on any part of this explanation or discuss any specific aspects of implementing these firewall rules?

---

