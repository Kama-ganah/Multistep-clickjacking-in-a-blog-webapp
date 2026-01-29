# Overview
During an assessment of the application’s account management functionality, I identified a high‑severity multistep Clickjacking vulnerability that allowed critical user actions to be performed without informed consent. The application relied on client‑side protections such as CSRF tokens and JavaScript confirmation dialogs, but failed to prevent user interface redressing. By embedding the target page inside a transparent iframe and carefully aligning decoy elements, a victim could be tricked into unknowingly completing both the account deletion action and its confirmation.

# Steps Undertaken

Step 1: Reviewed the account deletion workflow to understand required user interactions and protections.

Step 2: Observed that the delete action used a CSRF token and a JavaScript confirmation prompt.

Step 3: Embedded the account page inside an iframe and reduced its opacity to make it invisible to the user.

Step 4: Positioned decoy buttons over the real “Delete Account” and confirmation buttons using precise CSS alignment.

Step 5: Lured the user into clicking the decoy elements, triggering both deletion steps sequentially.

Step 6: Confirmed successful account deletion without the user realizing their true actions.

# Conclusion

This assessment confirmed a high‑impact multistep Clickjacking vulnerability affecting sensitive account operations. Despite the presence of CSRF tokens and confirmation dialogs, the lack of frame‑busting protections allowed attackers to manipulate user interactions and execute destructive actions. Proper anti‑clickjacking defenses, including frame restrictions and stronger server‑side validation of user intent, are necessary to prevent UI redressing attacks.
