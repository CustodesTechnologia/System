# The Server Upgrade Project

The goal if the project is as follows:
(not necessarily in this order, but close)

* Identify the new set of features to add to the site.
* Identify the current load on the system, calculate space and bandwidth requirements.
* Identify and design DDOS and adverse condition handling options on the new system.
* Estimate time-line (schedule) of when tasks can be completed, estimate date of site re-opening.
* Maintain and keep online all legacy data that has been accumulating in the Database (MySQL)
* Deploy a new server hardware system with capabilities to support the site.
* Migrate the current site data to the new system.
* Test and verify the legacy data is consistent on the new system.
* Verify collection of site metrics to have consistent and timely view of site performance.
* Reestablish able and reliable means to operate and maintain the system (backups, patches, etc...)
* Revise recruitment efforts made to staff the team of site system administration (not public facing)
* Scrub plans for appropriate level of detail for consumption by the general user base.

These goals are organized into phases.

## Phase 0 - Everything is Documented

We document everything.  We do not put secrets into documentation (like passwords), but we put all 
configuration, planning and task handling in a place we can all see and collaborate.

TBD More about how we intend to use tools to document plans, issues, bugs, tasks, etc..

## Phase 1 - Find out What we need

The initial phase is to find out precisely what requirements are for the new system.

The working list of capabilities we want to ensure exist (or add) are as follows:

1.  A Forum system to run-like existing Forum (posts, comments, etc..)
2.  A Gallery system to run-like existing Gallery (Pictures, etc.)
3.  A Blog system (new) to permit users to diverge from the Forum to document/review shared interests and projects.
4.  A Painter system (porting code) to permit users to experiment with model painting decisions.
5.  A "PM" system analogous to Mail to run-like existing PM capabilities.
6.  An internal ad/banner system to announce Events, Contests, Fundraising, for site wide benefit.

Other key capabilities of the site can be added or revised as we review the Phase 1 Goals.

This is a difficult phase to resolve only because the list of features we want is dependent on the kind
of system we are able to design.  In other words, if the Software we intend to license has no feasible support
for one of our site goals, then the cost to produce that 'plugin' to add to the site Software would be 
prohibitive. 

The choices we are intending to make for what capabilities we want are based on prior experience with the site
and the site Software.   So we have that advantage.   Unless the management team of the site decides to
add a whole new kind of capability not yet described, we should be OK with this list.

Edit the list to suit.

The other side of the Find out What question involves finding out the metrics of the current site usage:

1.  How many visitors
2.  How much data.
3.  Statistics on the load average of the system.
4.  Compare silicon benchmarks with the CPU we have with potential CPU's in data centers.
5.  How much space do we need to set aside for persistent storage.

Those data items are critical to know.


## Phase 2 - Application Software

Based on the decisions choosing which capabilities we want in the site, this next phase is a check-box
step to make sure the Software applications available to us will serve those purposes.

At the time of this writing, there is a preferred solution to maintain use of the Software we currently
use, but acquire a current version of that Software.   

The only other Software involved that is not available per se is the Painter software system -- which
I believe must be ported (ported, tested, integrated) into the new site Software.

It is expected that newer versions of MySQL will work seamlessly with supporting any of the schema enforced
by using Legacy Data with the Upgraded Software from IP.Board's vendor (Invision).

The preference is to main use of the "IP.Board" Software.   We are choosing to purchase the license
to self-host this Software.

The Pro:

1.  We already understand how it works.
2.  The cost to upgrade to a new version may be less than buying a new license for a different family of Software.
3.  Our database (legacy data) is already compatible with the Software.

The Con:

1.  It's expensive.
2.  It is not open source (ie., we cannot patch the software unless the Vendor provides a patch)
3.  It requires using the Legacy schema for the Database.

The bottom line on the Pro/Con is this:  If I were to start fresh with a new site, I would not choose IP.Board.
The cost and closed-source nature of the Software would rule it out.  There are actually a set of Free (open source)
alternatives that would be my first choice for the site Software.

Even if we were to go with commerical Software for the site, there are other Vendors with more active participation
with upgrading the Software.  XenForo comes to mind, and there are others.   

Having said all of that, the key requirement though is maintaining the existing Legacy Data.  That is what
attracts users to the current site.  It would be a fatal mistake to dismiss how important the Legacy Data is.
The cost (time) to convert the Legacy Data to any other schema would be a self-inflicted penalty towards
making the Upgrade as simple as possible.

Sticking with IP.Board makes the most sense.   It comes with some risk only in that we are depending on a third
party (the Vendor) to keep releasing patches to that Software.  Other than that, the Pro's outweigh the Cons.


## Phase 3 - New Server Hardware

Part of the Upgrade involves actually provisioning a new unit to be the Server Hardware.

There are a few issues to explore here.

1.  Where is it hosted (geographically is a concern), more so is a concern of how reliable and capable the network
it rests.  What kind of network backbone is present.
2.  Regardless of the location of the hosted server, the other issue is DDOS and Adverse Condition mitigation. 
Currently we use Cloudflare.  This would be a consistent thing to use in the Upgrade as well.  The upgraded server
hardware shall be integrated as to use Cloudflare as a reliable filter.
3.  The hardware itself -- the choice of silicon and arrangement of persistent storage (aka hard disks) is an
adjustable feature of the upgrade.    Unless the budget is clearly available, I would prefer not to waste money
on a SSD based Persistent Storage array.  Modern systems and caching is quite adequate.  But that depends on
the information collected about use and performance of the existing system.  We need to evaluate the data
about how many visitors we have, how much data we deliver and so on before we can rule out SSD vs HDD.  The cost
difference is significant.   However (again) if funding allows it, SSD is by far more performant.  I don't see
any reason to rule it out unless the data on usage proves otherwise.


## Phase 4 - Fitting the New Software to the New Hardware

This is the step where we acquire the new site Software license, install it on the New Hardware.

The phase then is about getting the fitment right for the Software on the Hardware and also begin the 
stepwise smoke testing of the Legacy Data with the updated System.

We'll need entire and complete MySQL dumps of the current database (date is not important, as long as it
is relatively current) and begin the process of trial (burn in) of the Legacy Data with the updated Software/Hardware.

This is a very time consuming process and honestly not exactly a process that can be proven to be "completed" unless
each and every piece of data is checked.  Every piece of data cannot be checked, that's the reality.

The process involves doing a careful study of the existing schema and the updated Software's schema and
analyzing the differences.   It involves careful SQL statement test-case writing to validate records migrated 
into the new Data Store match 1:1 with the records from the original Legacy Data Store.   This will involve
a fair amount of SQL script writing and validation tests to develop.

The caveat here is that the Legacy Data is mapped to a set of capabilities of the existing server.  The existing
server has Forums, Gallery.  I cannot think of any "dynamic - database dependent data" that the current site has.

So, the validation of the data migration is based on the current set of features.

After the validation is made, then that migrated-Legacy-Data becaomes the new baseline of the Upgraded Server.
That data (patched, not-patched, etc..) is more precious than the original.

Then, the trial begins -- adding the additional features to the upgraded Software (Blog's for instance) requires
re-validating the Database again.  And again, each time a new feature is added, tested and checked.

The point is, by adding new Software (plugins for Blog, for example), the profile of the Software System changes
and therefore the re-validation of the Persisted Data is required.


## Phase 5 - Adminstrative Glue and Process

At this point, the new Software is running with the updated and migrated Legacy Data.  All of the new
features are added to the Software and those in turn have been retested with the new baseline of Legacy Data.

At this point a collection of facts, and needs about how to adminstrate the system are gathered.

1. How backups are made.
2. How to apply backups.  (Like firedrills, this needs to be work perfectly, each time.  A backup is worthless if it cannot be used.)
3. Review of past experiences with the Site to make sure the Grimoire of knowledge is made for the Tech team.


More TBD


## Phase 6 - Annnoucement to Public

At this phase, the public users of the site may already be aware of the changes that are planned by rumor, but
the point at this phase is to disclose to the users what has been planned, what was implemented, and the timeline
for the public re-launch of the site on the new system.

This is important because the users of this site are invested in the site.  They may not all donate, but they
certainly "deposit" a great deal of content to the site.  And, that content is the treasure of the site. More
valuable than any donation.

So, coming clean with the user base is key -- key for their approval to keep using the site.  Key for their
interest in helping support the site financially as the needs arise for paying the bills.


A sub-phase to this is the planning and recruitment effort for adding to the Tech team.  This site requires
care and support and putting the responsibility on one person would be an obvious mistake.  So, the design of
this sub-phase is to establish a set of Roles and Responsibilities across the entire site (public facing
roles and non-public facing roles) -- document what the Role is, what they Do, and what their responsibilites
are. 

Then, once the Roles and Responsibilties are scrubbed, the Role for Tech needs to be examined carefully to
help devise a plan to recruit for members who are suitable to take that Role.   This may be easy..  This may not
be easy.  That is a question for long time administration of the site to reflect upon the history of the site
and the likelihood of findind recruits for the Tech Role as discussed.

##  Phase 7 - TBD

I am leaving a gap here in the plan to deal with a review of the Plan and choose to back-fill the plan
with issues that I may have overlooked.  The peer review of this plan is essential and I expect there to be
gaps -- gaps found by you, the reader -- and suggestions for improvement.



## Phase 8 - Cleanup

The site has been upgraded, the new server hardware has been switched over (DNS-wise) and now we are on
the new site.   Everyone is glad.

But there is cleanup to do.

The old legacy system needs to be preserved and stored for posterity.

The software scaffolding that was put up during the new server setup needs to be stowed (saved off) so that
the new Tech team is working within a cleanly labeled and wel documented process.


