### Q: My e-mail passed DMARC validation but stil getting into the SPAM folder.

We'll show you how to troubleshoot this a bit later but first things first: properly setup DMARC policy does not guarantee that your mail be classified as not SPAM. If you have such expectation I'd suggest you to keep reading but if you just don't care and want to troubleshoot skip to the end of the article.

While preparing this post I checked my Gmail's SPAM folder and found out there two messages from quite reputable senders: Airbnb and Whitehouse. They both passed DMARC validation but still Google thinks they are SPAM.

Sometimes DMARC is referred to (erroneously) as anti-spam technique and this sets improper expectations. But DMARC was born to fight spoofing not spam and these are totally different concepts.

DMARC protects your **From:** address from spoofing by:

1. authenticating your outgoing mail
2. providing an addressee with means to check if it's authenticated or not

While you can write DMARC policy which instructs your addressee to dump your unauthenticated mail into SPAM folder the opposite is not true. There is no such policy which could instruct an adressee to bypass her SPAM filter and place your authenticated mail right into Inbox.

Authentication is a simple technique and if this trick worked out all spammers would send authenticated spam to guarantee the delivery.

Therefore after adressee's MX performed DMARC validation it tosses your mail through the SPAM filter. If your DMARC policy does not instruct the addressee to reject or dump your unauthenticated mail then the SPAM filter decides for itself. Usually authenticated mail ranks better than unauthenticated so it has more chances to hit the Inbox but there is no guarantee.

#### Troubleshooting

1. First thing is to know is why exactly your mail goes into the SPAM folder. It might be DMARC related (if you setup your policy to **quaranteen** unauthenticated mail) but is usually related to poor content (e.g. your test mail has empty subject/body).

Send your mail to q2js3e@dmarchub.com and find below what our SPAM filter thinks of it.

2. If it's content related you'll have to work on your content. If it's your DMARC policy is who sending it to SPAM it means that your mail is not authenticated.
