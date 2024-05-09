
Search in video
0:00
hey guys and welcome back to a new video
0:01
in this video I will give you a guide on
0:03
Gradle version catalogs since they
0:05
become more and more the standard of
0:07
Gradle dependency management and to get
0:09
start with these all you really need to
0:10
do is to create a new empty Android
0:12
Studio project and here really depends
0:14
on when you watch this video so as of
0:16
now where the latest stable Android
0:18
studio version is Hedgehog version
0:20
catalogs are not the default yet when
0:22
you create a new product so if your
0:24
dependencies in your build.gradle app
0:26
file look like this where you have just
0:28
string dependencies right in here then
0:30
you're not yet using grad version
0:32
catalog and that also looks like that if
0:34
you're just using some kind of older
0:36
project that has been created with an
0:38
older Android studio version if you're
0:39
using one of the later Android Studio
0:41
versions so right now I think in Canary
0:44
it's iguana or so then Andro St will
0:46
already use and create such version
0:48
cataloges by default if you create a new
0:50
project in either way watch this video
0:52
so you really understand what these are
0:53
about and what you need to know in order
0:55
to use them only if your grad file looks
0:57
like this and you have your dependencies
0:59
as simple strings in your grad file then
1:01
you need to first of all create that
1:03
version catalog and in end the version
1:04
catalog is just a catalog of versions of
1:07
dependencies and the more dependencies
1:09
you have the more it becomes a pain to
1:11
manage these and to manage all these
1:12
different versions because some of your
1:14
dependencies might actually use the same
1:16
version if you have multiple
1:17
dependencies um of the same type for
1:19
example if you're using kto client for
1:21
networking that is a typical example you
1:23
might need a dependency for the for the
1:25
core of K your client you might need a
1:26
dependency for the authentication
1:28
feature you might need a dependenc for
1:31
logging HTTP calls and all these
1:33
dependencies are different but they use
1:35
and refer to the same version and
1:36
version catalogs just make that very
1:38
easy to manage that also if you have a
1:40
product with a multimodule structure we
1:42
have multiple grader modules and where
1:44
each single grader module has its own
1:46
set of dependencies a version catalog
1:48
allows you to have all your dependencies
1:49
at a single place which all modules can
1:52
refer to as a single source of Truth and
1:54
in the end if we take a look at such a
1:55
dependency in Android then that always
1:58
consists of the same parts so on the one
2:00
hand we have the so-call group which
2:02
comes before the colon so in this case
2:04
Android X core or Android X compos UI or
2:08
junit here that is really just a group
2:10
of dependencies so a group that bundles
2:12
multiple related dependencies so you can
2:14
see here Andro X compos UI and X compos
2:17
UI and X compos UI all these groups are
2:20
the same so all these dependencies
2:21
belong to the same group but they refer
2:23
to something specific relating to compos
2:25
UI so this is for the preview this is
2:28
for probably just normal compos
2:30
components and that's called the name so
2:32
what comes after the colon is the name
2:33
and then lastly after the last colon
2:36
potentially we have the version of a
2:38
dependency in this case here we don't
2:40
have a version specified so that is
2:42
another way of specifying a dependency
2:44
because here we use this B which stands
2:46
for bill of materials which includes all
2:49
the versions for a specific set of
2:50
dependencies so in this case um it's a
2:52
composed B which just combines a
2:54
specific set of versions for composed
2:56
dependencies that work well together and
2:59
if we specify such a b then we don't
3:01
need to specify the individual versions
3:03
for all these dependencies that are
3:05
contained inside of this and that way we
3:07
just need to update the version for this
3:08
B in order to update all the
3:10
dependencies that it includes okay so
3:12
much about the theory let's now create
3:13
our very first version catalog and again
3:16
if your Gradle file does not look like
3:17
this and you have something like lips.
3:19
androidx and so on here then you can
3:21
skip this step but if not you can go to
3:23
this project view here open your project
3:27
hiero key and go inside of this Gradle
3:29
folder because that is where the version
3:31
cataloges are located in here we want to
3:34
create a new file so right click new
3:36
file and we name that lips. versions. TL
3:41
that is how the default version catalog
3:43
is actually named We press enter and
3:45
then in here a version catalog is
3:47
structured into three parts usually
3:49
whoops which we introduce with such
3:52
square brackets on the one hand we have
3:53
versions block we then have a libraries
3:57
block and we then have a plugins block
4:00
So Below this versions block we specify
4:02
all the versions that we have for our
4:04
dependency so really just the version
4:06
1.7.0 and so on in this libraries block
4:08
we specify the dependencies we want to
4:10
use with these versions and in this
4:12
plugins block we specify the Gradle
4:13
plugins that we want to use so here in
4:16
our project file for example the
4:17
application plugin uh the cotland
4:19
compiler plugin if you're using dagger
4:21
Hil or so and that would also go in
4:23
there and so on for now you can see
4:25
Gradle wants us to synchronize these
4:26
changes let's do that click sync now and
4:28
when that is done when go back to our
4:30
app level Gradle file because you can
4:32
see now suddenly everything is
4:34
highlighted in yellow that means we can
4:37
do something here we can hover over such
4:38
a dependency and hit Alt Enter and you
4:42
can see we can now replace this with a
4:44
new library catalog declaration hitting
4:46
enter and that is now how we now specify
4:50
these dependencies that's currently
4:51
marked as an error because we need to
4:53
synchronized that before if we do that
4:56
then you will notice that the hour will
4:58
go away there you go and that is now how
5:00
we really refer to a specific dependency
5:02
that is specified in our version catalog
5:04
if we now take a look here in our Libs
5:06
version Tel file then that is exactly
5:09
what happened so Studio automatically
5:10
added the version for our core KTX
5:12
Library which is 1.12.0 and it also
5:15
added the Android xcore KTX dependency
5:18
where it specified the module so the
5:20
module is just the group together with
5:23
the name of our dependency and it
5:24
specified the version reference it
5:26
should use for that so here we say core
5:28
KTX because that is how the version for
5:30
that is called if now multiple
5:32
dependencies share the same qut KTX
5:34
version we don't need to Define that
5:35
multiple times no we can just paste the
5:37
same uh version reference here for all
5:40
these dependencies and the version
5:42
catalog will keep that in sync so if we
5:43
now go back and also do that for the
5:45
remaining dependencies here for the life
5:47
cycle runtime again Alt Enter and ENT
5:50
studio will create that version catalog
5:51
reference here Alt Enter again the only
5:54
dependency that doesn't automatically
5:56
work for yet is if you have such a bom
5:59
then you need to create that manually so
6:00
if we go to our lips. versions We need
6:02
to scroll up and actually refer or have
6:05
a version for the composed B version
6:08
which in this case is exactly this
6:10
version so we can copy this and paste it
6:13
in here and then under libraries we
6:15
specify the composed bill of materials
6:17
and the name convention for these
6:18
Library specifications is just exactly
6:21
like the version is called the
6:22
dependency is called you can see we have
6:24
Android X activity activity compose and
6:27
that's also how this is called so
6:28
Android X activity composed and whenever
6:31
there is a dash the version Library will
6:34
replace that with a DOT when we refer to
6:36
it here that way we have all
6:37
dependencies related to uh activities
6:40
here under lips. Android X activities we
6:43
have all dependencies related to Android
6:45
X under lips. Android X and so on so now
6:47
to specify this B we want to copy this
6:50
group and name
6:52
together we go in here and specify our
6:55
Android a. compose B Al Al open curly
7:00
braces here specify the module just like
7:02
above paste this here and we need to now
7:05
have a comma and refer to the version
7:08
with version. ref and in this case we
7:10
want to use our composed bomb version
7:12
and then in our build. gr app file we
7:14
can also sync this before so we don't
7:16
have any syntax errors we can go in here
7:19
and now replace this dependency in here
7:22
with lips. Android x. compost. bom when
7:26
we now want to use a dependency that
7:28
uses the version specified in the B like
7:31
here this composed UI dependency we can
7:33
again copy this go in here have an
7:37
Android x- compose D UI in this case we
7:41
only need to specify the group and not
7:43
the whole module because uh the version
7:45
is already specified in the B which
7:47
we've included so here we paste the uh
7:50
Android a composed. UI without the name
7:53
so just the whatever comes before the
7:55
colon and then we say the name is UI as
7:58
a separate dependency as a separate
8:00
parameter I mean um but here we don't
8:02
need to specify the version reference
8:03
because that is contained um by the
8:05
already included B and then again back
8:08
in our app level Gradle file we can now
8:10
refer to that with ellips uh Android x.
8:13
compost. UI If We sync this then
8:17
everything should be just fine let's do
8:19
this for the remaining compos
8:20
dependencies for that we can just go to
8:22
lips. versions can duplicate this one
8:25
here three more times on the one hand we
8:28
have our how was it called called UI
8:30
Graphics UI tooling preview so
8:33
ui- Graphics here we say okay we have
8:37
our composed UI that is the same but UI
8:39
Graphics isn't so again Android X compos
8:42
UI here we say UI Graphics here we have
8:44
UI Graphics
8:47
oops
8:49
Graphics tooling I think is it written
8:52
like that tooling preview actually u i
8:57
tooling pre preview you can see the auto
9:00
complete is also working here so UI
9:03
tooling preview then we have one for UI
9:07
material 3 we say that one is
9:12
material three we can sync this and then
9:15
we refer to these versions in our Gradle
9:17
file again I think the remaining
9:19
dependencies we can specify directly
9:21
with the shortcut in interal Studio I
9:23
hope they actually fix that so we can
9:24
also easily create that for the B and
9:27
for dependencies without
9:29
version but here we can say lips.
9:31
Android a. compost. ui. Graphics same
9:36
for the preview lips and X compose UI
9:43
toing preview and for the material one
9:47
as well lips Android X compose UI
9:51
material 3 then we can do junit out
9:54
enter enter again we can do this for the
9:58
junit extensions as well we can do this
10:00
for espresso and now since we used the
10:03
same B version for our instrumented
10:06
tests we can just refer to the same
10:09
reference from our version catalog so
10:10
lips do um Android x. compost. B and
10:15
that way we just have a single source of
10:17
Truth for that single dependency and if
10:19
that dependency changes the the version
10:21
for this bomb then this will
10:22
automatically update the dependency for
10:25
both the production and the instrumented
10:26
test APK and here it seems we still need
10:28
to add three more for instrument testing
10:31
and for the debu APK so on the one hand
10:34
we have Android X composed for UI test
10:37
junit 4 so let's just duplicate this
10:40
here UI junit
10:43
4 paste this here actually UI test-
10:48
junit 4 we have UI tooling let's put
10:52
this below the tooling preview so just
10:54
UI
10:57
tooling UI tool tooling and lastly we
11:00
have the UI tooling manifest I think so
11:04
UI
11:05
tooling manifest no is it UI test
11:08
manifest actually UI test manifest sync
11:12
now refer to these last few dependencies
11:18
here here it was what was that um UI
11:22
test J 4 lips Android X
11:27
junit uh no Android X X UI test what was
11:30
it called again uh UI test junit for and
11:34
X composed
11:36
UI lips andot X compose UI test junit 4
11:42
that one it is then we have one for and
11:46
X compos UI UI tooling and
11:49
x uh
11:51
lips and X compos UI tooling and lastly
11:57
the one for
12:00
anod X compos UI
12:04
tooling Manifest this one and that way
12:07
if we now sync this we successfully
12:09
migrated all of our dependencies to the
12:11
new version catalog where we now have a
12:13
single Source where we can update our
12:15
dependencies we're not done yet with the
12:16
video but just to show you here you also
12:19
get these highlights when there's a new
12:20
version and you can just hover over it
12:22
hit Alt Enter to change this version to
12:24
the latest stable version sync this and
12:27
it will sync these changes so with all
12:29
your Gradle modules we refer to the
12:32
version catalog like we do here and from
12:34
this point whenever you add a new
12:35
dependency to your project like here
12:37
let's say we want to add the extended
12:39
material icons for compos we say
12:41
implementation U material
12:44
icons extended I think it's this one
12:49
then you just add this you get the
12:51
Highlight you hit Alt Enter replace with
12:53
a library version catalog and you get
12:56
this in your version catalog you click
12:57
sync now and you're successful fully
12:59
added the dependency inside of your
13:00
version catalog however this is not the
13:03
only place where you have to deal with
13:05
versions another place is your Gradle
13:07
project file which is this one where you
13:09
have your Gradle plugins so you can see
13:10
the current Gradle version for your app
13:12
is in this case
13:14
8.2.1 so that has a version we have our
13:17
cotland version which is 1.9.0 in this
13:19
case so these are also kind of
13:21
dependencies that need to be managed and
13:23
luckily that also works with version
13:24
cataloges for which we can use this
13:26
plugins tab or this plugins section
13:29
below our dependencies up here for that
13:32
there is Sly no such shortcut as we have
13:34
for dependencies at least yet so we need
13:36
to just take these copy them over to our
13:39
lips
13:40
versions version catalog here and say
13:42
hey we have an Android
13:44
application which in this case has an ID
13:48
and we paste the ID here and we specify
13:51
the version reference with a new
13:54
reference we create for example AGP for
13:56
Android Gradle plug-in we go up here
13:59
here and create this here AGP version is
14:04
8.2.1 so exactly what we created here in
14:07
our um Gradle project file if we did
14:11
that we can sync now and to replace such
14:14
a Gradle plugin we now need to say lips.
14:18
plugins instead so not lips. androidx
14:20
but lips
14:22
plugins do Android application we don't
14:25
need to specify the version here since
14:28
that is contained in the version catalog
14:30
definition but we need to replace ID
14:32
with Alias and we can now do the same
14:34
for our carton version so just go in our
14:37
version catalog say Okay jet brains
14:40
cotlin or
14:42
so paste this
14:44
here version Catal version reference is
14:47
cotlin we say okay we actually have a
14:49
cotlin version here which is
14:52
1.9.0 in our case sync this go back to
14:57
our product file and we say Okay instead
15:00
of all this after the syn is successful
15:02
we say we have an alias lips plugins jet
15:05
brains cuton and same is actually the
15:07
case here in our app module where we
15:09
also have these plugins at the very top
15:11
so here we can also refer to Alias lips
15:15
plugins Android
15:16
application and lastly Alias lips
15:21
plugins jet bra cutland if we now sync
15:24
this then we completely migrated our
15:27
empty project from no version cataloges
15:29
to using version cataloges as I said in
15:32
newer Android Studio versions this will
15:33
be the default so the version catalog
15:35
will already be there with all these
15:37
standard composed dependencies but I
15:39
think it's still very important for you
15:41
to understand how that works so even if
15:43
you have an older project and you
15:45
migrate that you really understand where
15:47
this version catalog file is how how you
15:48
can create it how you can manually
15:50
create dependencies in there even though
15:52
there is some kind of support from end
15:54
studia at this point but you can see
15:55
even if we go inside of or activity um
15:58
then
16:00
our dependency oh no seems like one of
16:02
the dependencies isn't resolved or some
16:04
of them maybe the material one maybe I
16:07
miscopied something there composed UI
16:10
material and yes that's actually wrong
16:15
group needs to be Android X composed
16:17
material 3 not that one though um but
16:21
the material one where is it here
16:23
material paste this sync this and then
16:25
hopefully our dependencies are resolved
16:28
yes so everything is recognized just to
16:29
show you that this really works and
16:31
isn't just recognized in our grad files
16:33
but also directly in our main activity
16:36
awesome below this video you will find a
16:37
link to more advanced Android premium
16:39
courses so if you want to become an
16:40
industry ready Android developer these
16:41
courses are exactly for you so check
16:44
these out and other than that thanks so
16:45
much for watching this video I will see
16:47
you back in the next one have an amazing
16:48
rest of your week
16:57
bye-bye

