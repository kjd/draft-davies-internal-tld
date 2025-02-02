



Network Working Group                                          K. Davies
Internet-Draft                                                      IANA
Intended status: Informational                             A. McConachie
Expires: 21 July 2025                                              ICANN
                                                         17 January 2025


                   A Top-level Domain for Private Use
                    draft-davies-internal-tld-latest

Abstract

   This document describes the "internal" top-level domain for use in
   private applications.

Status of This Memo

   This Internet-Draft is submitted in full conformance with the
   provisions of BCP 78 and BCP 79.

   Internet-Drafts are working documents of the Internet Engineering
   Task Force (IETF).  Note that other groups may also distribute
   working documents as Internet-Drafts.  The list of current Internet-
   Drafts is at https://datatracker.ietf.org/drafts/current/.

   Internet-Drafts are draft documents valid for a maximum of six months
   and may be updated, replaced, or obsoleted by other documents at any
   time.  It is inappropriate to use Internet-Drafts as reference
   material or to cite them other than as "work in progress."

   This Internet-Draft will expire on 21 July 2025.

Copyright Notice

   Copyright (c) 2025 IETF Trust and the persons identified as the
   document authors.  All rights reserved.

   This document is subject to BCP 78 and the IETF Trust's Legal
   Provisions Relating to IETF Documents (https://trustee.ietf.org/
   license-info) in effect on the date of publication of this document.
   Please review these documents carefully, as they describe your rights
   and restrictions with respect to this document.









Davies & McConachie       Expires 21 July 2025                  [Page 1]

Internet-Draft        Private use top-level domain          January 2025


Table of Contents

   1.  Introduction  . . . . . . . . . . . . . . . . . . . . . . . .   2
   2.  Terminology . . . . . . . . . . . . . . . . . . . . . . . . .   2
   3.  Using the ".internal" Namespace . . . . . . . . . . . . . . .   2
   4.  Comparisons to Similar Namespaces . . . . . . . . . . . . . .   3
   5.  IANA Considerations . . . . . . . . . . . . . . . . . . . . .   3
     5.1.  Domain Name Reservation Considerations  . . . . . . . . .   4
   6.  Security Considerations . . . . . . . . . . . . . . . . . . .   5
   7.  Additional Information  . . . . . . . . . . . . . . . . . . .   6
   8.  Informative References  . . . . . . . . . . . . . . . . . . .   7
   Notes (for removal before publication)  . . . . . . . . . . . . .   8
   Authors' Addresses  . . . . . . . . . . . . . . . . . . . . . . .   8

1.  Introduction

   There are certain circumstances where private network operators may
   wish to use their own domain naming scheme that is not intended to be
   used or accessible by the global domain name system (DNS), such as
   within closed corporate or home networks.

   The "internal" top-level domain provides this purpose in the DNS.
   Such domains will not resolve in the global DNS, but can be
   configured within closed networks as the network operator sees fit.

   The "internal" top-level domain is intend to fulfil a similar purpose
   to the IP address ranges that are set aside for private-use (e.g.
   [RFC1918]).

2.  Terminology

   The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
   "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
   "OPTIONAL" in this document are to be interpreted as described in
   [BCP14] when, and only when, they appear in all capitals, as shown
   here.

   This document assumes familiarity with DNS terms; please see
   [BCP219].

3.  Using the ".internal" Namespace

   Network operators have been using different names for private-use DNS
   for many years.  This uncoordinated usage can result in
   incompatibilities or harm to Internet users.  For example, an
   organization might choose to use a name for this purpose that has not
   been assigned to them, which may later appear in the global DNS,
   thereby causing name collisions and undefined behavior for users.



Davies & McConachie       Expires 21 July 2025                  [Page 2]

Internet-Draft        Private use top-level domain          January 2025


   If an organization determines that they require a private-use DNS
   namespace, they should either use sub-domains of a global DNS name
   that is under their organizational and operational control, or use
   the "internal" top-level domain.  This document does not offer
   guidance on when a network operator should choose the "internal" top-
   level domain instead of a sub-domain of a global DNS name.  This
   decision will depend on multiple factors such, as network design or
   organizational needs, and is outside the scope of this publication.

   Note that DNSSEC validating resolvers will fail to resolve names
   ending in ".internal", as the name is not delegated in the root-zone.
   An organization wanting to use such names inside its organization MAY
   want to sign and validate names ending in ".internal", for example by
   using a local trust anchor.  The details of such a configuration are
   outside the scope of this document.

4.  Comparisons to Similar Namespaces

   Other namespaces are reserved for similar purposes, which
   superficially may seem to serve the same purpose as the "internal"
   domain, but are intended for different use cases.

   *  The "local" namespace [RFC6762] is reserved for use with the
      multicast DNS protocol.  This protocol allows for resolution
      between devices on a local network.  This namespace does not use
      typical DNS zones for name allocation, and instead uses the
      multicast DNS protocol to negotiate names and resolve conflicts.
      It is expected "internal" will be used for applications where
      names are specified in locally-configured zones.

   *  The "alt" namespace [RFC9476] is reserved for contexts where
      identifiers are used that may look like domain names, but do not
      use the DNS protocol for resolution.  This is in contrast to the
      "internal" domain which is to be used with the DNS protocol, but
      in limited, private-use, network scope.

   *  The "home.arpa" namespace [RFC8375] is reserved for use within
      residential networks, including the Home Networking Control
      Protocol [RFC7788].

5.  IANA Considerations

   The document requires no IANA actions.  For the reasons stated above,
   as the "internal" top-level domain is reserved from being used in the
   global DNS it MUST NOT appear in the DNS root zone.






Davies & McConachie       Expires 21 July 2025                  [Page 3]

Internet-Draft        Private use top-level domain          January 2025


5.1.  Domain Name Reservation Considerations

   { Edit note (WK): This is my proposed answers for the "Seven
   Questions" from RFC6761 - "Special-Use Domain Names"
   (https://datatracker.ietf.org/doc/rfc6761/).  I have put them here
   for review and discussion, _if_ it is decided that .internal
   qualifies as a special-use domain name. }

   *Note*:

   *  Answer 1: lifted RFC6762 - "Multicast DNS"
      (https://datatracker.ietf.org/doc/rfc6762/).

      -  I added an initial sentence to make it even more explicit.

   *  Answer 2: lifted from RFC6761 - "Special-Use Domain Names"
      (https://datatracker.ietf.org/doc/rfc6761/), Sec 6.5.  "Domain
      Name Reservation Considerations for Example Domains".

      -  I added text about potential special handling for cookies.

   *  Answers 3 and 4: lifted from RFC6761 - "Special-Use Domain Names"
      (https://datatracker.ietf.org/doc/rfc6761/), Sec 6.5.  "Domain
      Name Reservation Considerations for Example Domains".

   *  Answers 5 and 6: lifted from RFC6761 - "Special-Use Domain Names"
      (https://datatracker.ietf.org/doc/rfc6761/), Sec 6.1 "Domain Name
      Reservation Considerations for Private Addresses".

   *  Answer 7: lifted from RFC6762 - "Multicast DNS"
      (https://datatracker.ietf.org/doc/rfc6762/).

   1.  Users SHOULD understand that .internal names are not expected to
       be globally unique, and may resolve to different addresses and
       services on different networks. Since there is no central
       authority responsible for assigning .internal names, users SHOULD
       be aware of this and SHOULD exercise appropriate caution.  In an
       untrusted or unfamiliar network environment, users SHOULD be
       aware that using a name like "www.internal" may not actually
       connect them to the web site they expected, and could easily
       connect them to a different web page, or even a fake or spoof of
       their intended web site, designed to trick them into revealing
       confidential information.  As always with networking, end-to-end
       cryptographic security can be a useful tool.  For example, when
       connecting with ssh, the ssh host key verification process will
       inform the user if it detects that the identity of the entity
       they are communicating with has changed since the last time they
       connected to that name.



Davies & McConachie       Expires 21 July 2025                  [Page 4]

Internet-Draft        Private use top-level domain          January 2025


   2.  Application software, in general, SHOULD NOT recognize .internal
       names as special and SHOULD use .internal names as they would
       other domain names.  An exception to this may be web browsers
       (and similar) which may wish to institute special handling for
       cookies, such as invalidation when a network change is detected.

   3.  Name resolution APIs and libraries SHOULD NOT recognize .internal
       names as special and SHOULD NOT treat them differently.  Name
       resolution APIs SHOULD send queries for .internal names to their
       configured caching DNS server(s).

   4.  Caching DNS servers SHOULD NOT recognize .internal names as
       special and SHOULD resolve them normally.

   5.  Authoritative DNS servers SHOULD recognize these names as special
       and SHOULD, by default, generate immediate negative responses for
       all such queries, unless explicitly configured by the
       administrator to give positive answers for names within the
       .internal zone.

   6.  DNS server operators SHOULD, if they are using .internal names,
       configure their authoritative DNS servers to act as authoritative
       for these names.

   7.  DNS Registries/Registrars MUST NOT grant requests to register any
       of these names in the normal way to any person or entity.  These
       names are reserved for use in private networks, and fall outside
       the set of names available for allocation by registries/
       registrars.  Attempting to allocate one of these names as if it
       were a normal DNS domain name will probably not work as desired,
       for reasons 4, 5 and 6 above.

6.  Security Considerations

   While the namespace is designated for private use, there is no
   guarantee that the names utilized in this namespace will not leak
   into the broader Internet.  Since usage may appear in log files,
   email headers, and the like; users should not rely on the
   confidentiality of the "internal" namespace.

   As the "internal" namespace is not resolvable in the global DNS, it
   is not anticipated that Certificate Authorities will issue
   certificates for names ending in ".internal".  If an organization
   wants to use HTTPS with names ending in ".internal", they will need
   to use a private CA.






Davies & McConachie       Expires 21 July 2025                  [Page 5]

Internet-Draft        Private use top-level domain          January 2025


   Users should not expect that names ending in ".internal" are globally
   unique; it is likely that many of the same names will be used for
   entirely different purposes on different networks.  This is similar
   to the use of ".local" in the multicast DNS protocol - just as there
   are many different devices named "printer.local", there may be many
   different servers named "accounting.internal".  Users should be aware
   of this when entering credentials.  In addition, when diagnosing
   network issues, the appearance of such addresses must be interpreted
   with the associated context to ascertain the private network with
   which the name is being used.

   The lack of global uniqueness also has implications for HTTP cookies;
   a cookie set for "accounting.internal" on one network may be sent to
   a different "accounting.internal" (for example, if a user moves their
   laptop from one network using ".internal" to another network using
   ".internal").  This may be mitigated by adding the Secure flag to the
   cookie, but this requires that all users accessing the site have the
   required private CA installed and trusted on their device.

   (Ed note (WK): ... and that they don't also have a private trust
   anchor for the overlapping name on the other network that they join.
   This is really tricky to explain in an understandable way, and I
   think that it's enough of a corner case that I don't think it's worth
   trying to explain in this document.  Then again, the Security
   Considerations sections are often complicated, so perhaps it is?)

   Users should also not assume the appearance of such names is
   indicative of the true source of transmissions.  When diagnosing
   network issues, the appearance of such addresses must be interpreted
   with the associated context to ascertain the private network with
   which the name is being used.  A private-use name can never be used
   by itself to identify the origin of a communication.  It is entirely
   likely that many of the same names will be used for entirely
   different purposes on different networks connected to the Internet.

   (Ed note (WK): This is similar to my "don't assume uniqueness" above.
   I stole some of this text and reworded it, but am not sure that I
   captured all of it)

7.  Additional Information

   This reservation is the result of a community deliberation on this
   topic over many years, most notably [SAC113].  The SAC113 advisory
   recommended the establishment of a single top-level domain for
   private-use applications.  This top-level domain would not be
   delegated in the DNS root zone to ensure it is not resolvable in
   contexts outside of a private network.




Davies & McConachie       Expires 21 July 2025                  [Page 6]

Internet-Draft        Private use top-level domain          January 2025


   A selection process [IANA-Assessment] determined "internal" was the
   best suited string given the requirement that a single string be
   selected for this purpose, and subsequently reserved for this purpose
   in July 2024.  [ICANN-Board-Resolution]

8.  Informative References

   [BCP14]    Best Current Practice 14,
              <https://www.rfc-editor.org/info/bcp14>.
              At the time of writing, this BCP comprises the following:

              Bradner, S., "Key words for use in RFCs to Indicate
              Requirement Levels", BCP 14, RFC 2119,
              DOI 10.17487/RFC2119, March 1997,
              <https://www.rfc-editor.org/info/rfc2119>.

              Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC
              2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174,
              May 2017, <https://www.rfc-editor.org/info/rfc8174>.

   [BCP219]   Best Current Practice 219,
              <https://www.rfc-editor.org/info/bcp219>.
              At the time of writing, this BCP comprises the following:

              Hoffman, P. and K. Fujiwara, "DNS Terminology", BCP 219,
              RFC 9499, DOI 10.17487/RFC9499, March 2024,
              <https://www.rfc-editor.org/info/rfc9499>.

   [IANA-Assessment]
              "Identification of a top-level domain for private use",
              January 2024, <https://itp.cdn.icann.org/en/files/root-
              system/identification-tld-private-use-24-01-2024-en.pdf>.

   [ICANN-Board-Resolution]
              "Reserving .INTERNAL for Private-Use Applications", July
              2024, <https://www.icann.org/en/board-activities-and-
              meetings/materials/approved-resolutions-special-meeting-
              of-the-icann-board-29-07-2024-en#section2.a>.

   [RFC1918]  Rekhter, Y., Moskowitz, B., Karrenberg, D., de Groot, G.
              J., and E. Lear, "Address Allocation for Private
              Internets", BCP 5, RFC 1918, DOI 10.17487/RFC1918,
              February 1996, <https://www.rfc-editor.org/rfc/rfc1918>.

   [RFC6762]  Cheshire, S. and M. Krochmal, "Multicast DNS", RFC 6762,
              DOI 10.17487/RFC6762, February 2013,
              <https://www.rfc-editor.org/rfc/rfc6762>.




Davies & McConachie       Expires 21 July 2025                  [Page 7]

Internet-Draft        Private use top-level domain          January 2025


   [RFC7788]  Stenberg, M., Barth, S., and P. Pfister, "Home Networking
              Control Protocol", RFC 7788, DOI 10.17487/RFC7788, April
              2016, <https://www.rfc-editor.org/rfc/rfc7788>.

   [RFC8375]  Pfister, P. and T. Lemon, "Special-Use Domain
              'home.arpa.'", RFC 8375, DOI 10.17487/RFC8375, May 2018,
              <https://www.rfc-editor.org/rfc/rfc8375>.

   [RFC9476]  Kumari, W. and P. Hoffman, "The .alt Special-Use Top-Level
              Domain", RFC 9476, DOI 10.17487/RFC9476, September 2023,
              <https://www.rfc-editor.org/rfc/rfc9476>.

   [SAC113]   "SSAC Advisory on Private-Use TLDs", September 2020,
              <https://itp.cdn.icann.org/en/files/security-and-
              stability-advisory-committee-ssac-reports/sac-113-en.pdf>.

Notes (for removal before publication)

   *  It is currently assumed this domain should NOT be designated as a
      special-use domain name at https://www.iana.org/assignments/
      special-use-domain-names/ (https://www.iana.org/assignments/
      special-use-domain-names/).

   *  I-D source is maintained at: https://github.com/kjd/draft-davies-
      internal-tld (https://github.com/kjd/draft-davies-internal-tld)

Authors' Addresses

   Kim Davies
   Internet Assigned Numbers Authority
   Email: kim.davies@iana.org


   Andrew McConachie
   Internet Corporation for Assigned Names and Numbers
   Email: andrew.mcconachie@icann.org















Davies & McConachie       Expires 21 July 2025                  [Page 8]
