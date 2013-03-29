CHANGELOG
=========

* v.3.6-FUTURE
--------------
    - Fixed persistent XSS vulnerability in user self-editing (reported by
        Jean-Lou Hau)
    - Fixed persistent XSS vulnerabilities in AJAX object editing (reported by
        Jean-Lou Hau)
    - Fixed character set detection for ID3v1 tags
    - Added matroska to the list of known tag types
    - Made the getID3 metadata source work better with tag types that Ampache
        doesn't recognise
    - Switched from the deprecated mysql extension to PDO
    - stderr from the transcode command is now logged for debugging
    - Made database updates more robust and verified that a fresh 3.3.3.5 import
        will run through the updates without errors
    - Added support for external authenticators like pwauth (based on a patch by
        sjlu)
    - Renamed the local auth method to pam, which is less confusing
    - Removed the Flash player
    - Added an HTML5 player (patch by Holger Brunn)
    - Changed the way themes handle RTL languages
    - Fixed a display problem with the Penguin theme by adding a new CSS class 
        (patch by Fred Thomsen)
    - Made transcoding and its configuration more flexible
    - Made transcoded streams more standards compliant by not sending a random
        value as the Content-Length or claiming that ranged requests are
        supported
    - Changed rating semantics to distinguish between user ratings and the
        global average and add the ability to search for unrated items
        (< 1 star)
    - Updated Prototype to git HEAD (4ce0b0f)
    - Fixed bug that disclosed passwords for plugins to users that didn't
        have access to update the password (patch by Fred Thomsen)
    - Fixed streaming on Android devices and anything else that expects to
        be able to pass a playlist URL to an application and have it work
    - Removed the SHOUTcast localplay controller

*  v.3.6-Alpha4 2012-11-27
--------------------------
    - Removed lyric support, which was broken and ugly
    - Removed tight coupling to the PHP mysql extension
    - Fixed an issue with adding catalogs on Windows caused by inconsistent 
        behaviour of is_readable() (reported by Lockzi)

* v.3.6-Alpha3 2012-10-15
-------------------------
    - Updated getID3 to 1.9.4b1
    - Removed support for extremely old passwords
    - Playlists imported from M3U now retain their ordering
        (patch by Florent Fourcot)
    - Removed HTML entity encoding of plaintext email (reported by USMC Guy)
    - Fixed a search issue which prevented the use of multiple tag rules
        (reported by Istarion)
    - Fixed ASF tag parsing regression (reported by cygn)

* v.3.6-Alpha2 2012-08-15
-------------------------
    - Fixed CLI database load to work regardless of whether it's run from
        the top-level directory (reported by porthose)
    - Fixed XML cleanup to work with newer versions of libpcre
        (patch by Natureshadow)
    - Fixed ID3v2 disk number parsing
    - Updated getID3 to 1.9.3
    - Added php-gettext for fallback emulation when a locale (or gettext) isn't
        supported
    - Fixed pluralisation issue in Recently Played
    - Added support for extracting MBIDs from M4A files
    - Fixed parsing of some tag types (most notably M4A)
    - Corrected PLS output to work with more players (reported by bhassel)
    - Fixed an issue with compound artists in media with MusicBrainz tags
        (reported by greengeek)
    - Fixed an issue with filename pattern matching when patterns contained
        characters that are part of regex syntax (such as -)
    - Fixed display of logic operator in rules (reported by Twister)
    - Fixed newsearch issue preventing use of more than 9 rules 
        (reported by Twister)
    - Fixed JSON escaping issue that broke search in some cases
        (reported by XeeNiX)
    - Overhauled CLI tools for installation and database management
    - Fixed admin form issue (reported by the3rdbit)
    - Improved efficiency of fetching song lists via the API
        (reported by lotan_rm)
    - Added admin_enable_required option to user registration
    - Fixed session issue preventing some users from streaming
        (reported by miir01)
    - Quote Content-Disposition header for art, fixes Chrome issue
        (patch by Sébastien LIENARD)
    - Fixed art URL returned via the API (patch by lotan_rm)
    - Fixed video searches (reported by mchugh19)
    - Fixed Database Upgrade issue that caused catalog user/pass for
        remote catalogs to not be added correctly
    - Added the ability to locally cache passwords validated by external
        means (e.g. to allow LDAP authenticated users to use the API)
    - Fixed session handling to actually use our custom handler
        (reported by ss23)
    - Fixed Last.FM art method (reported by claudio)
    - Updated Captcha PHP to 2.3
    - Updated PHPMailer to 5.2.0
    - Fixed bug in MPD module which affected toggling random or repeat 
        (patch from jherold)
    - Properly escape config values when writing ampache.cfg.php
    - Fixed session persistence with auth disabled (reported by Nathanael
        Anderson)
    - Fixed item count retention for Advanced Random (reported by USAF_Pride) 
    - Made catalog verify respect memory_cache
    - Some catalog operations are now done in chunks, which works better on
        large catalogs
    - API now returns year and bitrate for songs
    - Fixed search_songs API method to use Search::run properly
    - Fixed require_session when auth_type is 'local'
    - Catalog filtering fix
    - Toggle artwork with a button instead of a checkbox (patch from mywindow)
    - API handshake code cleanup, including a bugfix from postfuturist
    - Improved install process when JavaScript is disabled
    - Fixed duplicate searching even more
    - Committed minor bugfixes for Penguin theme
    - Added Fresh theme
    - Fixed spurious API handshake failure output

* v.3.6-Alpha1 04/27/2011
-------------------------
    - Fixed forced transcoding
    - Fixed display during catalog updates (reported by Demonic)
    - Fixed duplicate searching (patch from Demonic)
    - Cleaned up transcoding assumptions
    - Fixed tag browsing
    - Added new search/advanced random/dynamic playlist interface
    - byterange handling for ranges starting with 0 (patch from uberbrady)
    - Fixed issue with updating ACLs under Windows (reported by Citlali)
    - Add function that check ampache and php version from each website.
    - Updated each ampache header comment based on phpdocumentor.
    - Fixed only admin can browse phpinfo() for security reasons on /info.php
    - Added a few translation words.
    - Updated version 3.6 on docs/*
    - Implemented ldap_require group (patch from eliasp)
    - Fix \ in web path under Apache + Windows Bug #135
    - Partial MusicBrainz metadata gathering via plugin
    - Metadata code cleanup, support for plugins as metadata sources
    - New plugin architecture
    - Fixed display charset issue with catalog add/update
    - Fixed handling of temporary playlists with >100 items
    - Changed Browse from a singleton to multiple instances
    - Fixed setting access levels for plugin passwords
    - Fixed handling of unusual characters in passwords
    - Fixed support for requesting different thumbnail sizes
    - Added ability to rate Albums of the Moment
    - Added ability to edit/delete playlists while they are displayed
    - Fix track numbers not being 0 padded when downloading or renaming.
    - Rating search now allows specification of operator (>=, <=, or =)
        and uses the same ratings as normal display.
    - Add -t to catalog_update.inc for generating thumbnails
    - Generate Thumbnails during catalog art operations
    - Fixed transcode seeking of Flacs by switching to MM:SS format for
        flacs being transcoded
    - Change album_art_order to art_order to reflect general nature of
        config option
    - Fix PHP warning with IP History if no data is found.
    - Add -g flag to catalog update to allow for art gathering via cmdline
    - Change Update frequency of catalog display to 1 second rather then
        %10 reduces cpu load due to javascript excution (Thx Dmole)
    - Add bmp to the list of allowed / supported album art types
    - Strip extranious whitespace from cmdline catalog update (Thx ascheel)
    - Fix catalog size math for catalogs up to 4TB (Thx Joost.t.Hart@planet.nl) 
    - Fix httpq not correctly skipping to new song 
    - Fix refreshing of localplay playlist when an item is skipped to
    - Fix missing Content-Disposition filename= on non-transcoded songs
    - Fix refresh of localplay playlist when you delete a track from it
    - Added ability to add Ampache as a search descriptor (Thx Vlet)
    - Correct issue with single song downloads
    - Removed old useless files
    - Added local auth method that uses PHP's PAM module
    - Correct potential security issues due to misuse of REQUEST for write
        operations rather then POST (Thx Raphael Geissert <geissert@debian.org>)
    - Finished switching to Dba::read() Dba::write() for database calls
        (Thx dipsol)
    - Improved File pattern matching (Thx october.rust)
    - Updated Amazon Album art search to current Amazon API specs (Thx Vlet)
    - Fix typo that caused song count to not be set on tag xml response
    - Fix tag methods so that alpha_match and exact_match work
    - Fix limit and offset not working on search_songs API method
    - Fix import m3u on catalog build so it does something
    - Fix inconsistent view during catalog operations    
    - Sort malformed files into "Unknown (Broken)" rather then leaving
        them in "Unknown (Orphaned)"
    - Fix API democratic voting methods (Thx kindachris)
    - Add server version to API ping response
    - Fix Localplay API methods (Thx thomasa) 
    - Improve bin/catalog_update.inc to allow only verify, clean or add
        (Thx ascheel)
    - Fix issue with batch download and UNC paths (Thx greengeek) 
    - Added config option to turn caching on/off, Default is off
    - Fix issue where file tag pattern was ignore if files have no tag structure
    - Add TDRC to list of parsed id3v2 tags
    - Added the rating to a single song view
    - Fix caching issue when updating ratings where they would not
        display correctly until a page reload
    - Altered the behavior of adding to playlists so that it maintains
        playlist order rather then using track order
    - Strip excessive \n's from catalog_update (Thx ascheel)
    - Fix incorrect default ogg transcode target in base config file
    - Fix stream user preferences using cached system preferences 
        rather then their own 
    - Fixed prevent_multiple_logins preventing all logins (Thx Hugh)
    - Added additional information to installation process 
    - Fix PHP 5.3 errors (Thx momo-i)
    - Fix random methods not working for localplay
    - Fixed extra space on prefixed albums (Thx ibizaman)
    - Add missing operator on tag and rating searches so they will
        work with other methods (Thx kiehnet@netscape.net)
    - Add MusicBrainz MBID support to uniqly identify albums and
        also get more album art (Thx flowerysong)
    - Fix the url to song function
    - Add full path to the files needed by the installation just to 
        make it a little clearer
    - Fixed potential endless loop with malformed genre tags in mp3s
        (Thx Bernhard Weyrauch)
    - Fixed web path always returning false on /test.php
    - Updated Man Page to fix litian problems for Debian packaging
    - Fixed bug where video was registering as songs for now playing
        and stats
    - Add phpmailer and change ampache.cfg.php.dist
    - Fixed manpage (Thx Porthose)

* v.3.5 05/05/2009
------------------
    - Added complete Czech translation (Thx martin hason)
    - Add the AlmightyOatmeal-Sanity check to prevent a clean from
        removing all songs if your mount failed, but is still
        readable by ampache
    - Make the Lang Install page prettier
    - Added Check for hash,inet_pton,windows PHP Version to init so
        that upgrades without pre-reqs are handled correctly
    - Allow mms,mmsh,mmsu,mmst,rstp in Radio Stream URLs
    - Fixed a problem where after adding a track to a saved playlist
        there was no UI response upon deleting the track without
        a page refresh
    - Fix an issue where the full version of the album art was never
        used even when requested
    - Fix maxlength on acl fields being to small for all IPv6 addresses
    - Add error message when file exists but is unreadable do not
        remove unreadable songs from catalog
    - Fixed missing title tag on song browse for the title 
        (Thx flowerysong)
    - Fix htmlchar'd rss feed url
    - Fix Port not correctly being added to URL in most cases
        even when defined in config
    

--------------------------------------------------------------------------
  v.3.5-Beta2 04/07/2009
    - Fix ASX playlists so more data shows up in WMP (Thx Jon611)
    - Fix dynamic playlist items so they work in stream methods again
    - Fixed Recently played so that it correctly shows unique songs
        with the correct data
    - Fix some issues with filenames with Multi-byte characters 
        (Thx Momo-i)
    - Add WMV/MPG specific parsing functions (Thx Momo-i)
    - Add text to /test.php for hash() and SHA256() support under PHP
        section
    - Fix SHA256 Support so that it references something that exists
    - Fix incorrect debug_event() on login due to typo
    - Remove manage democratic playlist as it has no meaning in the 
        current version
    - Run Dba::reset_db_charset() after upgrade in case people are playing
        hot potato with their charsets. 
    - Move Server Preferences to Admin menu (Thx geekdawg)
    - Fixed missing web_path reference on radio creation link
    - Fixed remote catalog_clean not working
    - Fixed xmlrpc get image. getEncoding wasn't static 


--------------------------------------------------------------------------
  v.3.5-Beta1 03/15/2009
    - Add democratic methods to api, can now vote, devote, get url
        and the current democratic playlist through the api
    - Revert to old Random Play method
    - Added proxy use for xmlrpcclient
    - Added Configuration 'Wizard' for democratic play
    - Fixed interface feedback issues with democratic play actions
    - Add extension to image urls for the API will add to others as
        needed due to additional query requirement. Needed to fix
        some DLNA devices
    - Fixed typo that caused the height of album art not to display
    - Modified database and added GC for tmp_browse table
    - Added get lyrics and album art using http proxy server #313 
        + username, password patch
    - Added lyricswiki link Ticket #70
    - Updated README language
    - Updated getid3 library 2.0.0b4 to 2.0.0b5
    - Make the Democratic playlist be associated with the user
        who sends it to a 'player' 
    - Fixed missing page headers on democratic playlist
    - Show who voted for the sogns on democratic playlist
    - Increase default stream length to account for the fact that movies
        are a good bit longer then songs
    - Correct Issues with multi-byte characters in Lyrics (Thx Momo-i)
    - Added caching to Video
    - Added Video calls to the API
    - Remove redundent code from Browse class by making it extend
        nwe Query class
    - Update Prototype to 1.6.0.3
    - Add Time range to advanced search
    - Add sorting to Video Browse
    - Changed to new Query backend for Browsing and Dynamic Playlists

--------------------------------------------------------------------------
  v.3.5-Alpha2 03/08/2009
    - Fixed caching of objects with no return value
    - Fixed updating of songs that should not be updated during catalog
        verify
    - Added default_user_level config option that allows you to define
        the user level when use_auth is false. Also allows manual
        login of admin users when use_auth is false. 
    - Fix Version checking and Version Error Message on install (Thx Paleo)
    - Moved Statistics to main menu, split out newest/popular/stats
    - Fixed bug where saved Thumbnails were almost never used
    - Fixed Localplay HTTPQ and MPD controls to reconize Live Stream
        urls. 
    - Added Localplay controls to API 
    - Added Added/Updated filters to API include the ability to specify
        a date range using ISO 8601 format with [START]/[END]
    - Changed API Date format to ISO 8601 
    - Fixed Incorrect Caching of Album records that caused the 
        Name + Year + Disk to not be respected
    - Added Lyrics Patch (Thx alister55 & momo-i)
    - Fixed password not updating when editing an HTTPQ localplay
        instance
    - Added Video support
    - Fixed normalize tracks not re-displaying playlist correctly
    - Fixed now playing now showing currently playing song
    - Fixed now playing clear all not correctly refreshing screen
    - Fixed adding object to playlist so that it correctly shows the 
        songs rather then an empty playlist
    - Added User Agent to IP History information gathering
    - Added Access Control List Wizards to make API interface
        setup easier
    - Added IPv6 support for Access Control, Sessions, IP History 
    - Fixed sorting issue on artist when using search method
    - Updated flash player to 5.9.5
    - Fixed bug where you admins couldn't edit preferences of
        users due to missing 'key' on form
    - Added Mime type to Song XML 

--------------------------------------------------------------------------
  v.3.5-Alpha1 12/31/2008
    - Fixed sort_files script so that it properly handles variable
        album art file names in the directories
    - Fixed issue where small thumbnails were used for larger images
        if gd based resizing was enabled in the config
    - Fixed catalog_update.inc so it doesn't produce errors
    - Made democratic play respect force http play
    - Make installation error messages more helpful
    - Added Swedish (sv_SE) translation (Thanks yeager)
    - Allow Add / Verify of sub directories of existing catalogs
    - Prevent an fread of 0 bytes if you seek to the end of a file
    - Added require_localnet_session config that allows you to exclude
        IP(s) from session checks, see config.dist 
    - Added Nusoap (http://sourceforge.net/projects/nusoap/) library
        for use with future lyrics feature
    - Fixed problem with flash player where random urls were not being
        added correctly
    - Fixed problem with user creation using old method (Thx Purdyk)
    - Switched to SHA256() for API and Passwords
    - Added check for BADTIME error code from Last.FM and correctly
        return the error rather then a generic one
    - Fix http auth session issues, where every request blew away the 
        old session information
    - Many other minor improvements (Thx Dipsol)
    - Fixed warnings in caching code (Thx Dipsol)
    - Massive text cleanup (Thx Dipsol)
    - Fixed tag searching and improved some other search methods to 
        prevent SQL warnings on no results
    - Improved Test page checks to more accuratly verify putENV support
    - Make network downsampling a little more sane, don't require 
        access level
    - Added caching to Playlist dropdown 
    - Fixed double caching on some objects
    - Added base.css and 4 tag 'font' sizes depending on weight/count
    - Fixed inline song edit
    - Updated registration multi-byte mail.
    - Fixed vainfo.class.php didn't catch exception for first analyze.
    - Fixed iconv() returns an empty strings (Thx abs0)
    - Updated getid3 for multi-byte characters, but some wrong id3tags
        have occurred exception error.
    - Fixed use_auth = false not correctly re-creating the session if
        you had just switched from use_auth = true
    - Add links to RSS feeds and set default to TRUE in config.dist
    - Fixed Dynamic Random/Related URLs with players that always send
        a byte offset (MPD)
    - Added Checkbox to use existing Database
    - Updated language code and Fixed catalan language code
    - Added Emulate gettext() from upgradephp-15
        (http://freshmeat.net/p/upgradephp)
    - Fixed Test.php parse error.
    - Updated multibyte character strings mail.
    - Fixed To send mail don't remove the last comma from recipient.
    - Updated More translatable templates.
    - Removed merge-messages.sh and Add LANGLIST (each languages 
        translation statistics).
    - Fixed If database name don't named ampache, can't renamed tags
        to tag.
    - Fixed count issue on browse Artists (Thx Sylvander)
    - Fixed prevent_multiple_logins, preventing all logins (Thx hugh)
    - Fixed Export catalog headers so it corretly prompts you to download
        the file
    - Add ability to sort by artist name, album name on song browse
    - Implemented caching on artist and album browse, added total
        artist time to the many artist view
    - Fixed test config page so it bounces you back to the test page
        if the config starts parsing correctly
    - Fixed browsing so that you can browse two different types in two 
        windows at the same time 
    - Improved gather script for translations (Thx momo-i)
    - Added paging to the localplay playlist
    - Updated German Translation (Thx Laurent)
    - Fixed issue where Remote songs would never be removed from
        the democratic playlist
    - Fixed issue where user preferences weren't set correctly
        on stream (Thx lorijho)
    - Added caching of user preferences to avoid a SQL query on load
        (Thx Protagonist)
    - Fixed home menu not always displaying the entire contents
    - Fixed logic error with duplicate login setting which caused it
        to only work if mysql auth was used
    - Changed Passwords to SHA1 will prompt to reset password
    - Corrected some translation strings and added jp_JP (Thx momo-i)
    - Ignore filenames that start with . (hidden) solves an issue
        with mac filesystems
    - Fix tracking of stats for downloaded songs 
    - Fix divide by 0 error during transcode in some configurations
    - Remove root mysql pw requirement from installer
    - Added Image Dimensions on Find Album Art page
    - Added Confirmation Screen to Catalog Deletion
    - Reorganized Menu System and Added Modules section
    - Fix an error if you try to add a shoutbox for an invalid object
        (Thx atrophic)
    - Fixed issue with art dump on jpeg files (Thx atrophic)
    - Fixed issue with force http play and port not correctly specifying
        non-standard http port (Thx Deathcrow)
    - Remember Starts With value even if you switch tabs
    - Fixed rating caching so it actually completely works now
    - Removed redundent UPDATE on session table due to /util.php
    - Added Batch Download to single Artist view
    - Added back in the direct links on songs, requires download set
        to enabled as it's essentially the same thing except with
        now playing information tied to it
    - Bumped API Version to 350001 and require that a version is sent
        with handshake to indicate the application will work
    - Removed the MyStrands plugin as did not provide good data, and does
        not appear to have been used
    - Added Catalog Prefix config option used to determine which prefixes
        should not be used for sorting
    - Merged Browse Menu with Home
    - Added checkbox to single artist view allowing you to enable/disable
        album art thumbnails on albums of said artist
    - Added timeout override on update_single_item because the function
        is a lie
    - Fix translations so it's not all german
    - Genre Tag is now used as a 'Tag', Browse Genre removed
    - Ignore getid3() iconv stuff doesn't seem to work
    - Improved fix_filenames.inc, tries a translation first then strips
        invalid characters 
    - Fixed album art not clearing thumbnail correctly on gather 
    - Fixed localplay instance not displaying correctly after change
        until a page refresh
    - Fixed endless loop on index if you haven't played a song in 
        over two years
    - Fixed gather art and parse m3u not working on catalog create
        also added URL read support to m3u import
    - Upped Minimum requirements to Mysql 5.x
    - Add codeunde1load's Web 2.0 style tag patch
    - Fixed typo in e-mail From: name (Thx Xgizzmo)
    - Fixed typo in browse auto_init() which could cause ampache to not
        remember your start point in some situations. (Thx Xgizzmo)

--------------------------------------------------------------------------
  v.3.4 05/10/2008 
    - Fixed an issue where the plugins could be installed infinite times
        if you kept refreshing the install page causing them to break
    - Fixed a problem with creating new preferences using the class
        functions, and also looking up setable preferences
    - Fixed user creation allowing empty password, when login prohibits 
        login without a password
    - Fixed an issue with the config file generation and upped the config
        file version to force everyone to get new config files. 
    - Tweak Pruning of Temporary Playlists so it only happens sometimes, 
        not on every single login. This might lead to a larger db but
        should increase login speed
    - Fixed an issue where the prefixes on albums were not being included
        when checking for an existing album. 
    - Fixed get recently played not correctly limiting to specified user
        (Thx Xgizzmo)
    - Fixed lack of refresh of controls when switching between localplay
        and other play methods
    - Add Debug page with current configuration and php state information
        as well as links to generate new config file and reset database
        charset
    - Fixed lack of loading indication during catalog processes
    - Fixed flash player not working if playlist_method included clear
    - Fixed album art thumbs never saving due to incorrect table reference
    - Fixed download having no filename if no catalog pattern
    - Fixed issue where 0 sized images could be inserted into the database
        artificially inflating its size
    - Added Playlist and Genre Counts to the XMLAPI Handshake
    - Added ability to Add Search Results to playlist, or download
        if batch download is enabled
    - Fixed Remove one vote, removes all votes on democratic play
    - Fixed sorting issue on Browse Users

--------------------------------------------------------------------------
  v.3.4-Beta3 04/20/2008 
    - Fixed Rating display and Rating Advanced Search
    - Added ability to specify new Genre when adding a Radio Station
    - Fixed Recently Played to do Distinct over last X rather then
        distinct over all time
    - Added update the attempts to correct the charset on the db
        columns
    - Added prompt for input charset to fix_filenames.inc
    - Updated Links in Readme
    - Fixed Show Art filter on browse by albums
    - Added Ratings links to Browse Albums and Browse Artist
    - Fixed seeking on random track, giving you a new track every    
        seek 
    - Added additional error reporting if localplay access / config
        fails
    - Give Admins Full Localplay Regardless
    - Fixed incorrect reference to ellipsis thresholds 
    - Fixed page point not being remembered by the back button
    - Fixed naming restrictions on database name during install
    - Fixed issue where verify updated all songs in the catalog even
        if there was no change
    - Fixed recently played, only shows distinct songs
    - Fixed enabling of localplay modules, now correctly enables
        localplay for the activating user
    - Added single genre and playlist XML methods
    - Changed error message on XML api, now based of HTTP error codes
    - Split out ACL and Session Expire errors on XML API 
    - Made Alpha Match box on browse "find as you type" (Thx Spocky)
    - Modified Shoutbox Styles (Thx Spocky)

--------------------------------------------------------------------------
  v.3.4-Beta2 03/16/2008
    - Added Cooldown Functionality to Democratic Play
    - Added /bin/fix_filenames.inc for correcting filenames with
        invalid chars
    - Removed album art add on Verify now that there is a distinct
        action for it 
    - Added ICONV check to ensure filenames are of correct charset 
        before inserting into the database
    - Fixed issue with encoding of id3v1/v2 tags
    - Fixed an issue with the clean function for playlists
    - DB Update, fixes the playlist create issue with full strict on
        MySQL 5.x
    - Corrected mime type for JPG (Thx CoF)
    - Added Catalog Last Update and Last Add times to API Handshake. 
    - Fixed Remember Me Cookie so it's actually set
    - Removed some invalid queries that were not needed, tweaked logic
        of no_session to avoid useless query
    - Added Greek Translation ( Thx Panayotis Tsirigotis )
    - Fixed browse issue when adding filters under specific conditions
    - Removed ip2int, int2ip and replaced with standard PHP functions
    - Updated Russian Translation and plural fixes ( Thx littlesavage )
    - Fixed Sorting on Admin->Browse Users
    - Fixed Shoutbox and shoutbox management (pb1dft)
    - Fixed some minor glitches in user registration ( pb1dft )
    - Fixed typo that caused mail to always mail to everyone. 
    - Fixed an issue with user auth in XML API always registering as
        system (Thx purdyk)
    - Fixed issue with Update All and multiple catalogs not correctly
        reseting changed album set
    - Added ability to filter disabled songs from duplicate check on 
        by default (Thx joh6nn) 
    - Added new rating images (Thx greengeek)
    - Added check for old database versions, prevent upgrade if too old
    - Fixed issue with user creation (Thx yoog)
    - Fixed Now Playing refresh
    - Fixed single song update (Thx alex2008)
    - Added Checkbox for All Playlists filter (Admin Only) also made
        filters only appear when its logical for them to be there
    - Fixed filtering of Private Playlists and fixed editing of type
        of playlist. Default is still public on creation. 
    - Fixed erroneous fseek() when downsampling. 
    - Fixed search by stars so that it returns the correct results 
        (Thx alex2008)
    - Fixed issue where random didn't end correctly when no results found
    - Fixed mime type never being updated on verify and added language
        and lyrics to gather from id3v2
    - Implemented a semi-working write_tags.inc script limited by getid3()
        support (Thx tomatopi)
    - Added limit option to the XML API
    - Fixed an issue where inline song editing wouldn't update the song 
        title (Thx profner)
    - Fixed conf error on registration confirmation and made it
        aware of greylisting
    - Fixed Admin Preference Level updates
    - Fixed incorrect command for skip to on HttpQ (Thx usaf_pride)
    - Fixed problem with gif and png resize
    - Fixed problem where democratic play wouldn't send to localplay
        and would just display a blank screen
    - Added Multi-Character Filter on browse pages
    - Fixed Flag Management Interface
    - Added Export Catalog to CSV
    - Added 'Add New...' option to other fields on Song Edit (Thx picasso)
    - Fixed incorrect index on localplay playlist after track deletion
    - Fixed lack of high-light of current playing item on localplay
        playlist
    - Fixed problem where second send to MPD would invalidate all 
        previous songs on the playlist
    - Fixed LastFM album art gather so it ignores noimage results from 
        lastfm
    - Fixed downsample remote so that is downsamples those not in the
        network def rather then those inside the network def
    - Fixed issue with page-a-nation on show catalogs page
    - Fixed removal of rating from db when 'unrating' the object (Thx flashk)
    - Fixed Itunes Export (Thx flashk)
    - Fixed session start failure when use_auth is off and you have
        no pre-existing cookie
    - Fixed print_tags.inc file to catalog matching, now fuzzy like it
        should be
    - Fixed bug where file pattern would be ignored if there were no
        tags in file
    - Replaced " " with "\s" on Pattern Match Logic
    - Removed extra space on default Last.FM username/password
    - Fixed LastFM plugin username and password checking to not even try
        if there is no username or password

--------------------------------------------------------------------------
  v.3.4-Beta1 12/25/2007 
    - Added Metadata (.directory or desktop.ini) when using the 
        /bin/dump_album_art.inc file
    - Added 'Add New...' option to Album on Song Edit (Thx picasso)
    - Fixed multiple login check 
    - Fixed filters applying incorrectly to non-browse displays
    - Fixed Flash Player issue when Playlist Method wasn't default
    - Fixed XML-RPC, now uses handshake method properly
    - Fixed bug where stream would start even with no songs
    - Upgraded to Prototype 1.6
    - Added playlists and playlist_songs methods to API
    - Fixed a problem with the javascript that was causing Opera to not
        get the playlist correctly. 
    - Migrated to 'new' auth system that unifies xml-rpc,api and normal
        sessions in a single table
    - Fixed some issues with downsampling + seeking and seeking in 
        general (Thx Karl Hungus) 
    - Fixed CSS references to missing files
    - Fixed Missing Levels on Edit and incorrect level on edit
    - Added check to make sure timestamp passed to API is less then
        four hours old. Set to four hours to allow for some 
        difference in server/client time
    - Fixed basic XML-RPC functionality, using insecure / old 
        authentication method needs more work
    - Fixed it so that all errors should return an XML document when
        using the XML API. 
    - Added Basic ShoutBox functionality, needs formating fixes
        and needs to be moved to a better spot in classic theme it
        must be turned on in the /config/ampache.cfg.php
    - Fixed Mail functions, some features from old mail are missing for
        now. 
    - Fixed Delete Disabled & Sort Files command line scripts
    - Fixed Find Duplicates Functionality
    - Added Highest Rated option to Advanced Random
    - Fixed incorrect mime type being set on ASX playlists
    - Fixed problem where you couldn't change playlist type 
        (Thx Karl Hungus) 
    - Fixed potential issue with display on some preferences
    - Added Length to Advanced Random and removed Minutes from methods 
    - Added function exists check for session with redirect to /test.php
        on failure
    - Fixed incorrect extension and stream command being sent when using
        transcode for type other then mp3
    - Fixed default flac downsample command, removed -r as flac decode
        appears to not be raw pcm
    - Fixed download filename to match the catalog filename pattern
    - Added downloads back to stats tracking 
    - Fixed disable/re-enable of users
    - Fixed a bug where ajax actions wouldn't trigger a redirect to login
        when session expired, instead they would just break
    - Fixed a bug with Random Play if you had no artists/albums/playlists
    - Fixed Admin's ability to modify other users preferences
    - Added User and Manager levels to Localplay, determines what the
        user in question can do
    - Moved Newest * to statistics page
    - Database Update, removed useless config options and tweaked a few others
    - Fixed last of the missing MPD functionality (Volume & Playlist Clear)
    - Fixed HTTPQ and improved parsing for urls from MPD & HTTPQ
        they now recognize Democratic Playlists
    - Added paging to genre sub-pages
    - Added missing song data fields to single song view
    - Fixed display issue with playlists when deleting a song
    - Fixed sorting of 'add to Playlist' menu on rightbar
    - Added another layer of checking on catalog deletes to help 
        prevent orphaned elements
    - Fixed lack of prefix on Albums, improves album art search 
        results (Thx darkside)
    - Fixed problem with invalid urls populated to localplay methods
        under certain conditions
    - Fixed Album Art dump bin script 
    - Added paging to the Playlist Song view
    - Fixed error on catalog Update All 
    - Fixed Public registration page, and simplified logic
    - Added 'Add' button to recently played
    - Limited Rightbar to only 100 items, adds last row indicating any
        additional items on playlist. Prevents Firefox crash if you
        add many thousands of items to a single active playlist
    - Corrected Sorting of Democratic Play votes, sort order is now 
        # of votes then oldest vote first so new votes sort to
        the bottom
    - Fixed sending URLs directly to MPD
    - Fixed a problem with automatic downsampling which was referencing
        a now non-existent function 
    - Massive speed improvement on display and sorting of standard
        browse functions
    - Put Ratings back into single song view 
    - Corrected potential consistency issue with Play Type dropdown
    - Made Access Denied page more friendly, added verbage for
        demo access

--------------------------------------------------------------------------
  v.3.4-Alpha3 11/25/2007 
    - Fixed display problem and lack of link when creating a catalog
    - Initial Version of Democratic play working, minor speed improvements
        to normal tmpplaylist class due to simplification and removal
        of democratic related code
    - Added ability to do batch downloads on the FS failed downloads
        currently will not be garbage collected (Thx COF)
    - Added default mime type if none found (image/jpg) 
    - Changed XML-RPC ACL type to RPC to reflect multiple uses
    - Tweaked catalog add function to improve speed (Thx Karl Hungus)
    - Added XML API borrows authentication style from Last.FM's 
        scrobbling, allows query of Ampache DB, returns XML
        see http://ampache.org/bugs/wiki/XmlApi
    - Added tweak for Wii so that Flash player opens in current window
        (Thx Dgn)
    - Fixed bug where Ampache would incorrectly search for album art
        when config option was empty (Thx Karl Hungus)
    - Enabling a Localplay Method will now set Allow Localplay to true
    - Fixed all playlist methods, send, send and clear and clear on 
        send now work correctly
    - Added single song view
    - Added Play Select drop down back in
    - Fixed ordering of catalogs
    - Fixed multi-genre Random Play
    - New Version of Flash player fixes playlist repeat bug (Thx hugoh)
    - Fixed catalog update and album art dump command line tools
    - Removed dead link for renaming an Artist
    - Fixed batch download of a single album
    - Added reset of filters when switching between browse types this
        may be removed in the future...
    - Fixed LastFM submitting even when there was no username/password
    - Put Catalog 'All' Functions back onto catalog view
    - Fixed Admin Preferences reverting to user after first update
    - Fixed Localplay playlist
    - Updated Ajax Load icon (Thx Spocky) 
    - Replaced Flash Player with Lacy Morrow's (http://blog.lacymorrow.com/)
        (Thx Hugoh)
    - Fixed ACL's
    - Fixed incorrect Mime type being passed with transcoded songs due 
        to duplicate headers being passed
    - Fixed an issue where MPD was clearing all but last song in submit
        if its initial state was not play 
    - Added check for PHP5 to prevent ugly errors if missing
    - Fixed issue with NULL localplay controller causing fatal error
    - Fixed the Localplay Controls
    - Fixed Gathering album art to only gather for changed albums
    - Fixed display of catalog to correctly show catalog stats
    - Gather album art now only gathers for the specified catalog
    - Fixed Random methods (rightbar) 
    - Added Loading box for ajax actions
    - Added ability to append to existing playlists
    - Modified Play Method to use hidden iframe
    - Fixed album random and by min random 
    - Added Delete to Playlist and Live Streams (Radio)
    - Massive improvements to CSS (Thx Spocky) 
    - Addition of Greysme theme (Thx Spocky)
    - Basic MPD Support Restored
    - Moved catalog stats off to statistics page
    - Added basic sorting to all browse pages
    - Tweaked the Playback to try to fix some issues with WMP
    - Reduced the timeout on the LastFM Plugin to reduce delay
        when scrobbling is down
    - Added Add buttons to single playlist view, and put the delete 
        link back for catalogs
    - Fixed Playlist Play links
    - Added ability to gather album art for a single catalog at a time
    - Improved Upgrade Documentation
    - Disabled more functionality when in Demo Mode because people
        are lame
    - Cleaned up Preferences, moved Plugin Preferences into their own
        section
    - Fixed potential LastFM issue if invalid data is passed
    - Added Abstract class for localplay and started work on 
        next generation of localplay support
    - Moved Catalog functions out of sidebar, back into the content
        area
    - Fixed a problem with batch downloads and tmpplaylists
    - Fixed missing set_timeout_limit(0); on add to catalog
        functions

--------------------------------------------------------------------------
  v.3.4-Alpha2 09/03/2007
    - Fixed a problem where it'd let you go through the install after
        ampache had already been installed due to a change in the
        config variable names
    - Added ability to delete songs from a saved playlist
    - Added ability to create a new playlist based on active playlist
    - Fixed the Playlist Method 'Send on Add' so that it works, the
        'Send and Clear' is still broken
    - Fixed Advanced random
      - Fixed missing artist name on Albums of the Moment
    - Added simple Playlist element view, non-editable
      - Fixed double posting of songs on a single stream with some
        clients
      - Updated LastFM protocol to v1.2 
    - Fixed copyright notices (Thx porthose)
      - Fixed single downloads
      - Fixed weird CSS issue with a crafty little hack
      - Fixed a session fixation issue
      - Fixed Album Disk support for OGG's and added display to browse
        albums
      - Added Album Disk support for id3v2 (Thx Hugo Haas)
      - Updated LastFM pluging, must uninstall/reinstall to make it work
        will add in auto-update later
      - Adjusted LastFM reporting to reduce lag between songs. You must
        now currently be logged in for LastFM to report correctly
      - Fixed a potential PHP error when browsing the last page or a 
        search with 0 results
      - Fixed rating search method
      - Added 'Buy This Track' link on Find Missing Tracks if a purchase
        url is given in the returned data
      - Reduced # of pages at any one point on browse pages and tweaked
        their display, and fixed the bottom paging stuff
      - Massive improvement to sidebar (Thx Spocky) 
    - Added default sort order for Song Titles, Albums & Artists
        has a dbl sort bug, leaving it in until true sorting
        is in so you can click twice to invert sort
      - Added Find Missing tracks, requires MyStrands
      - Added ability to show Album art on Browse -> Albums
      - Added Similar Artists Link, requires MyStrands
      - Fixed hovering on the static Ratings displays
      - Added MyStrands Plugin, must be enabled under Plugins
      - Re-enabled / updated Plugin functionality
      - Fixed CSS (Thx Spocky) 
      - Added Playlists as a browse type and fixed playback
      - Fixed an issue where albums of the moment would show when you 
        had 0 albums
      - Fixed warnings on Update & typo in Install
      - Removed redundant GPL licence file
      - Fixed filesize() issue on config re-gen
      - Fixed an issue with seeking causing incorrect stats counts 
    - Fixed a potential issue with the kajax.js and checkboxes
    - Added 'Advanced Search' link to top rightbar
    - Added Paging to bottom of all views
    - Fixed get_location() (Thx ichneumon)
    - Moved Quick search to the top, right appears on every page
    - Fixed an issue with reading id3tags causing a uncaught exception
        due to direct reference to getid3() 
      - Added check on clean to see if Root path is readable, if not
        stop clean (mount point failures) 
      - Fixed now playing, hopefully once and for all
      - Added distinct sessions for each stream action, also allows
        for independent session lengths between interface
        and streaming
      - Added paging on all song displays including search
      - Fixed searching via quicksearch bar
      - Added 'Your' playlists to leftbar with play and view links
      - Fixed clear now playing
      - Fixed now playing issues with Audacious 1.3.x office space style

--------------------------------------------------------------------------
  v.3.4-Alpha1 07/29/2007
    - Improved Albums of the Moment performance on large catalogs
        (Thx Vlet)
      - Added Migration script for config file. Also added in sane
        redirection on config parse failure
      - Added initial dynamic playlist item support, only default
        and genre work right now. 
    - Added support for Internet Radio Stations
    - Updated LastFM submission formating to account for changes on 
        last.fm (Thx entropathy)
    - Fixed LastFM and increased timeout slightly in an attempt to 
        improve success rate
    - Disabled Search, Random Play & Localplay for Alpha release
    - Replaced CC Flash player with the previous GPL based flash player
        used patched 0.2.3 version created by Sylvain of 
        http://www.jamendo.com/fr/
    - Round the downsampled content-length
      - Fixed cataloging so that Orphaned Albums are always the same year
      - Added new preferences, created new Playlist Preference section
    - Fixed Find album art so it can look in the id3/wma art tags 
        correctly (Thx Karl Hungus)
      - Updated SQL to latest version
      - Moved Album art out of the album table into album_data 
      - Changed Browsing Method and default playlist method
      - Added Play links for Favorite Artists/Albums/Songs
      - Fixed an issue with the random album selection that was causing
        a full table scan, which could lead to poor performance
        with large databases
      - Start of Complete rewrite, config file format changed, requires
        manual re-creation of /config/ampache.cfg.php
    - Updated French and German translations
      - Added min song count to Browse Artist, referencing min object count
        preference
      - Fixed ratings so that it shows your rating if you've rated it
        otherwise it shows an average rating
      - Fixed Democratic Play newest votes of same total count first
        (Order by vote time)
    - Fixed a problem where config re-gen wouldn't update the current
        version
    - Changed database to fix some user tracking issues
    - Added date to user_vote to allow for sorting by vote date on 
        democratic play
    - Added Label, Catalog # and Language to song extended data table

--------------------------------------------------------------------------
  v.3.3.3 01/26/2007 
    - Updated the SQL file for stable release
    - Fixed an issue with having db album art method always returning
        true and returning a non-array
    - Fixed a race condition with downsampling and transcoding
    - Fixed some refresh issues on the localplay page
    - Fixed a redirect to a blank page if you hit play selected when
        nothing was selected (Thx Chenb)
    - Added detection of old config files, message displayed to admins
        upon login
    - Fixed an issue with WMP11 and Lock Songs that prevented playback
        due to the way Now Playing was being calculated
    - Fixed comment searching, broken when split out into its own
        table
    - Fixed a issue with Catalog builds in Windows 
    - Fixed a bug with admins ability to set the preferences of a 
        specific user
    - Fixed logic on force http that was causing it not to work under
        specific configurations
    - Fixed a flagged and rated item clean issue with catalogs
    - Fixed some minor issues in HttpQ and MPD localplay controllers
      - Fixed Album Art search on Catalog add so that it only searches
        albums that currently don't have art
      - Fixed a long outstanding issue with Windows Shared drives and
        the incorrect slashes and speed up catalog builds a tiny
        bit
    - Improve speed, sanity of single album art search
    - Fixed a logic issue with force_http_play
    - Improved performance of Amazon album art search by reducing the
        queries made on gather album art
    - Fixed an issue with all numeric usernames
    - Fixed some minor catalog cleaning issues that could arise due
        to the order of the clean functions
    - Added missing functions to the HttpQ controller, should now have
        all capabilities that MPD has. 
    - Fixed minor ajax issue with localplay buttons
    - Fixed issue with Add to Catalogs always searching for all
        album art making it really slow
    - Fixed typo in session management that prevented setting of
        secure_cookie option (used default value)
    - Added ability to e-mail flagged/disabled reports in mail 
        functions (Thx PB1DFT)
    - Fixed flagging not correctly tracking user on flag creation
    - Added select boxes to Admin Flag pages to allow rejection or
        approval of all songs at once
    - Fixed an XMLRPC catalog issues created when I moved comments
    - Fixed an issue with localplay controls showing up even if it
        was disabled
    - Fixed Album of Moment's title tag and prevented it from showing
        albums without art (Thx Spocky)
    - Fixed a play issue on democratic play created when I added
        the menu
      - Fixed batch page to correctly show access denied rather then
        redirecting on error
    - Fixed Genre actions to actually work
    - Added http://www.famfamfam.com icons to browse functions
      - Fixed Flash Player now playing issue
      - Fixed a img resize logic error that could cause no art to
        display if resize was on and resize failed
      - Added Albums of the Moment to the Front page and removed the
        stats information
      - Moved Popular/Recent to /stats.php and made Browse by Song the
        default browse action
      - Fixed missing clean of Genre stats information and a logic
        flaw with order of clean functions in the catalog clean 
      - Fixed Localplay page appearing even if disabled by Admin Config
        if user still had distinct permissions
      - Added Menu to TV page per request
      - Fixed Album Art Upload and Cover URL methods
      - Fixed play lock with Democratic Play if song no longer exists
      - Fixed a display issue of the Now Playing on the Democratic
        play page
      - Fixed display of Last IP if track_user_ip was disabled
      - Fixed Update to redirect to test.php if no db connection found
        (Thx SpComb)
    - Fixed an issue that caused AJAX not to work if you were working
        in a sub-directory. 

--------------------------------------------------------------------------
  v.3.3.3-Beta3 01/04/2007 
    - Fixed a few more unhandled mis-configurations of Localplay which
        could cause PHP errors
    - Fixed an issue with the Quick Jump box on Browse by Songs
        (Thx Jru)
    - Tweaked Headers passed for AJAX in an attempt to 'help' IE. 
      - Last Database update before Stable
      - Fixed a view issue introduced when sorting of the albums under
        single artist view was added 
      - Removed unused options from config file
      - Fixed some remaining album art issues and a undefined array()
        issue if you only have one user and try to view 
        recommendations
    - Fixed some get_info() references in song.class.php that caused
        XBMC to not work. 
    - Added Die,Das,Ein,Eine as prefix's for album names (Thx Vogi)
    - Added reading of riff tags 
    - Improved Sidebar CSS making it more compliant with different
        browsers (Thx Spocky)
    - Fixed some logic errors in the Transcoding logic and play logic
    - Rewrote Album Art collection to correct some serious logic flaws
    - Added potential fix for FastCGI installations
    - Updated Snoopy to 1.2.3 (from manually patched 1.2.1) 
    - Fixed sorting of Themes, now sorted by Alpha of theme name
    - Fixed long standing Now Playing display issue in Classic Theme
    - Fixed Now Playing to account for Windows Media Player 11s 
        3 HTTP Requests per song stupidity
    - Added ability to mass tag using play selected functionality
    - Fixed Preferences page, preferences now ordered semi-logically
    - Fixed MPD controller so it displays track numbers correctly
    - Added HttpQ Localplay Module. 
      - Added 'Best Guess' option to Duplicate Song Disabled that checks
        the shortest, lowest bitrate, smallest of a duplicate set
      - Removed unused templates and documents
    - Added ability to edit artist/albums and flag all songs under them
        for re-tagging. 
    - Fixed charset of XML documents returned (Thx blueorder)
    - Fixed ORDER BY `track` that was missing on play selected and 
        reduced it to a single query, rather then one per object
    - Fixed ip history being tracked even if disabled in config
    - Improved performance of icon rendering due to increased use
    - Added error handling for if /config/ampache.cfg.php.dist is 
        not readable
    - Added new Icons from http://www.famfamfam.com from the Silk
        subset. (Thx kalrnux && Mark James)

--------------------------------------------------------------------------
  v.3.3.3-Beta2 12/18/2006: 
    - Fixed a bug that prevented adding new songs to the catalog.
    - Removed a upload preference that I missed.
    - Timezone setting actually works


--------------------------------------------------------------------------
  v.3.3.3-Beta1 12/18/2006 
      - Moved Comment information to separate table and added lyrics
        row, no support for lyrics yet though.
      - Removed Upload functionality (broken, and time better spent on
        other features)
      - Added Recommendations based on Ratings to Stats page
      - Encoded the LastFM password so that it isn't displayed or
        stored in plain text. 
      - Fixed an issue with Admin -> Streaming -> Localplay Level
        not correctly displaying the current setting
      - Integrated LastFM plug-in per user requests. 
    - Added /bin/delete_disabled.php.inc to delete any disabled
        songs in your DB, defaults to Debug only mode
    - Fixed display issue with players that ignore EXTINF in m3us
        (Thx AlxRogan)
    - Added Refreshing to the Recently Played menu at the same time
        it refresh the now playing on the index page
    - Fixed a cataloging issue that was using a round about way of
        checking to make sure the song wasn't flagged. 
    - A ton of CSS cleanup (Thx apex)
    - Fixed an issue with multi-value config options on test.php
    - Changed default site_charset to UTF-8 in ampache.cfg.php.dist
    - Fixed some <? in show_test.inc (Thx apex)
    - Added Plug-in Interface under Admin --> Modules
    - Fixed play type switcher so it shows all possible play methods
    - Tweaked home page a little, remove pop songs and recent artists
    - Added Recently Played to Main Page
    - Fixed an issue on Browse by Albums and sorting by Artist after
        sorting by something else 
    - Added initial Tag writing script (Thx Jirwin)
      - Updated flag class to make it easier to create a tag writer
      - Fixed some potential issues with sort_files.php.inc
    - Added the ability to Upload a M3u and have it attempt to build
        a playlist based on the filenames
    - Added the ability for admins to 'Push' the democratic link
        to a play method/localplay instance
    - Fixed a bug with the File tag_order method
    - Fixed a problem with Localplay Skip to song and added 
        highlighting of currently playing song
    - Added new Flash Player with full support for Non-US Char and 
        colors. (Thx PB1DFT/Enrico Lai http://www.enricolai.com)
    - Tweaked how MPD is handled, if MPD is stopped a new play action
        will clear old playlist, otherwise Play appends. 
        (Thx henrik)

--------------------------------------------------------------------------
  v.3.3.3-Alpha2 11/12/2006
    - Added Export to Itunes DB function (Thx PB1DFT)
    - Fixed some Ajax Issues, added Now Playing to TV page
    - Fixed album art search on every Catalog Add
    - Added exception to MPD controller, forces HTTP play regardless
    - Added From File: option to album art (Thx pb1dft)
    - Updated French Translation (Thx charrea)
    - Tweaked default config, Ratings are enabled by default
    - Added Genre link on show_songs along with some other minor UI
        improvements
    - Added Export to Itunes DB function (Thx PB1DFT)     
    - Fixed Show All of Song Titles not having any data
    - Fixed override of local_length to 9000 regardless of config file
    - Tweaked Remember Me Checkbox to be disabled if remember_length
        is <= local_length
    - Fixed issues with date not being set on insert of stats
    - Fixed style issue on Single Album view when ratings are off
    - Added Democratic Play ability, UI incomplete and 'clunky'
    - Added some extra error checking to the install process
    - Fixed issue with delete confirmation on playlist always being 
        yes, even if you click no.
    - Added more error checking to install, won't let you continue 
        without a valid MySQL connection, rather then relying
        on the db_select() to fail
    - Fixed a session race condition if you turn use_auth off and on
        and a user log in while use_auth if off
    - Fixed a potential foreach error if no songs passed to stream
        now logs error and gently returns the user
    - Added ability for Admins to define the required permission level
        for individual preferences
    - Added WavPack support
    - Forced a sane Post Size had some people with 32 byte post sizes
        which will not work with Ampache. 
    - Fixed a logic error with the MPD controller.
    - Fixed a problem were invalid bitrates below the set downsample
        bitrate could cause lame to crash as they weren't 
        validated. 
    - Added XSPF Flash player, rough around the edges but it works
        (Thx pb1dft/GrinningArmor)
    - Fixed bug with Album --> Artist sorting, wasn't allowing you to
        sort Z-A
    - Fixed bug with most popular where links weren't being generated
        correctly


--------------------------------------------------------------------------
  v.3.3.3-Alpha1 10/28/2006
    - Added IP History to admin->users (Thx pb1dft)
    - Added HTTP auth method, auto-creates a 'user' if the auth user
        doesn't exist in the database. 
    - Fixed Mail statistics. It broke down after earlier updates.
    - Reworked RSS features (Thx pb1dft)
        Newest and latest songs albums and artist are available 
        through RSS.
    - Reworked Stats so that they are time specific, allows for 
        Top 10 of this week, threshold is per user configured
    - Added Admin Allow XXXX preferences for downsampling, streaming
        localplay and democratic play
    - Added Generate Config tool for admins to update their configs
        to the latest version. It reads current settings and merges
        with the new config file and prompts for a download
    - Added PutENV check on test page to make sure we can redefine
        memory limit and safemode is off
    - Added Russian translation (Thx Dimon) 
    - Fixed a problem with vainfo ignoring file pattern if no other
        tags were found
    - Added new version of getid3() library which will hopefully 
        resolve some PHP5 related issues
    - Fixed security issue that allowed users to gain guest access to
        ampache if register globals is enabled. 
    - Added xml based query for artists,genre,albums and search see
        /server/xml.server.php
    - Fixed false positive error and PHP5 related error on archive
        creation
    - Added <image> tag for album art and ability to filter rss feed
        by user by adding ?username=<username> to rss link.  
    - Added LDAP/Active Directory  auth support (Thx Rubin & pb1dft)
    - Added ajax support to ratings, no longer requires a refresh, 
        hello instant gratification. 
    - Tweaked Kajax, now accepts an array of elements to replace
        from a passed xml document. allows for multiple targets
        on a single ajax request 
    - Fixed display of disabled localplay methods, Preferences will
        now only display active ones. 
    - Fixed MPD Controller to attempt to find files based on filename
        if they were added outside of ampache
    - Tweaked Now Playing to prevent wrapping of Album Art.
    - Tweaked stylesheet to fix problem with Firefox and the :active
        style on the sidebar with the select drop downs
    - Added Options to Mail statistics to users when sending them
        a message (Thx pb1dft)

--------------------------------------------------------------------------
  v.3.3.2 10/01/2006
    - Updated SQL file, changed default site title
    - Fixed Duplicate Songs functions that have been broken for a 
        while
    - Fixed some Install issues with incorrectly named templates
    - Added check for MySQL support to first install page, redirects
        to /test.php if mysql support is non-existent
    - Added ability to turn Random/Repeat on and off in localplay
        and also improved localplay page a tiny bit.
    - Fixed a problem with pagination on the admin/users.php page
    - Added ability to turn on User/IP/Date Login history tracking 
        viewable only by Administrators
    - Fixed issue with IE not being able to download files with ? or
        / or \ in their filenames, replaced with _
    - Added New ACL system which allows user based ACL's  and 
        introduces shared keys for xml-rpc communication and 
        local/remote network definitions for auto-downsampling
    - Introduced new Theming method and 'migrated' all old themes in
        /contrib results may vary. (Thx Ros)
    - Added ability to search by Rating, requires MySQL 4.0 or above
    - Page headers now limited to 30 pages with [....] between top
        and bottom 15.
    - Added Browse by Title functionality (Thx Rubin)
    - Added Min Album size as preference, defaults to 0 (Thx Rubin)
    - Fixed a problem with the automatic registration sorting on user
        lists and admin notification of new users (Thx pb1dft)
    - Fixed 'auto_user' config option on automatic registration it
        wasn't actually respecting the config option (Thx pb1dft)
    - Fixed Implemented XSPF playlist generation (Thx pb1dft)
    - Fixed an issue with 'Download Selected' from playlists passing
        the incorrect songs
    - When adding to a playlist by default it 'appends' rather then
        integrating (Thx Salguod)
    - Now Remembers the Last used playlist correctly. (Thx Salguod)
    - Cleaned up some Formating issues with the Access control 
        interface.
    - Fixed an issue with the MPD Controller not passing the password
        to the MPD class causing flames to shoot out if your MPD
        had a password set.
      - Fixed issue with transcoding not changing the mime type or the
        filename, currently hardcodes to mp3 and audio/mpeg.
      - Updated Spanish Translation (Thx Bgordon)
    - Fixed potential for a foreach() error on vainfo if no tags are
        found, and fixed quicktime (mp4) tag reading.
      - Fixed the CSS for now playing, with multiple entries it turned
        into modern art. 
      - Fixed issue with Keywords search that cropped up when I removed
        the checkboxes. 

--------------------------------------------------------------------------
  v.3.3.2-Beta3 06/22/2006
      - Fixed file-based parsing so that it can now be given priority
        over the tags in the files using tag_order in the config
        file
      - Fixed Now playing, now div based layout and AJAX refreshed
        based on config files refresh_limit
      - Moved /modules/init.php to /lib/init.php
    - Removed Checkboxes from Search page and added ability to 
        search on Comment and Rating
      - Fixed a missing close tag on the catalog build if ampache was
        unable to get the filesize of a file
      - Fixed link to Statistics page, user link has been missing
        since the new interface was put into place
      - Added new getid3() wrapper (vainfo) should resolve the
        id3 tags in oggs issue that some people were having
        and makes file only tag basis possible. requires
        and update to your ampache.cfg.php
      - Fixed Transcoding logic issue and added preset line for
        transcoding flac files in .dist file (Defaulted to Off)
      - Upgraded to Getid3() 1.7.6
      - Fixed an issue where the new song->get_url() wasn't respecting
        the force_http_play, this also fixes a long outstanding
        bug with localplay + https + force_http_play
      - Added PCRE check on /test.php and updated to use Ros's new
        spiffy theme
      - Added pruning of empty playlists (Admin Only)
      - Fixed error on /login.php when theme isn't set which caused
        a fopen failure to show up in the logs
      - Improved MPD class to use PHP 4.3+ socket timeout settings so
        that if your MPD server goes down while in MPD mode it
        doesn't hard-lock ampache. 
      - Suppressed deprecated var warnings in PHP5
      - Fixed link to playlist import
    - Fixed playlist add on every catalog add (I'm not kidding this 
        time... really..)
      - Fixed Access Control List so that it prevents Login if you are
        not inside the allowed range. 
      - Fixed Localplay/Stream Buttons so that they also work if you
        have use_auth disabled
      - Added Icecast Controller (Thx Nikk)
      - Added Clear Playlist Functionality to Localplay
      - Added Language selection to Installer (Thx Ros)
      - Added xbmc controller, restricted to playback of mp3s shared 
        over samba (Thx Infamy)
      - Fixed a problem where if require_session was disabled it would
        still pass the sid with the urls
      - Fixed problem where jpegs wouldn't get resized (Thx blueorder)
      - New Install and Update screen styles (Thx Ros)
      - Fixed a glitch that was causing m3u's to be built on every 
        catalog add, rather then just on creation
    - Tweaked Preferences once more
    - Added Modules Page, used for enabling/disabling localplay
        types
      - Fixed a missing web_path reference on playlist edit page
    - Added Localplay API, check the wiki for more information
        http://ampache.org/bugs/wiki/Localplay
      - Added Download to Random play along with Size limitation
        useful for downloading a set amount of music for your
        mp3 player.
      - Fixed mime detection, wasn't strtolowering the value
    - Fixed a few more Charset issues specifically with Russian 
        (Thx Nikk)

--------------------------------------------------------------------------
  v.3.3.2-Beta2 03/29/2006
      - Fixed some Charset problems with htmlentities (Thx Nikk)
    - Fixed some issues with IE and session caching (Thx wishbone)
      - Improved Upload Error Messages and blanked up upload and 
        quarantine directories for non-admin users
      - Added horrible hack to make Artist sorting work in the Album 
        browse page, this is temp until Ampache 3.4
      - Fixed a problem with the playlist update confirmation page
      - Fixed css issues with preferences (Thx WarrenG) 
      - Added dump album art command line script and tweaked catalog
        build display.
      - Tweaked preferences adding tab'd views rather then all on one
        page, also added account page back in. 
      - Fixed popen in downsample, forcing binary mode, so that windows
        works correctly (Thx SoundOfEmotion)
      - Tweaked some defaults in .dist config file as well as the error 
        handler, in order to account for debug_level
      - Added catalog drop down back to quick random play form
      - Added bandwidth throttling to downloads, must be enabled in config
        (Thx pb1dft)
      - Added loose name compare and rename functions to help with sorting
        similar artist names (Thx SpComb)
      - Fixed a problem with not being able to add Albums to a playlist
        (Thx eudaimon)
      - Fixed a problem with browsing genres that would incorrectly put
        'Browse' in the Showing Genres Starting With: box
      - Fixed some unescaped ID's in class constructors. 
      - Added debug_level config option to allow fine tuning of logging
      - Fixed catalog functions hopefully increasing speed and removing a bug
        with fast search
      - Fixed cookie code to account for violation of RFC's by IIS 5 where
        in IIS 5 fails to send cookie header on a header redirect
        (Thx Paul Webb)
      - Fixed verification of Batch Downloading, if ZLIB isn't detected it
        will not even give you the link
      - Added remember_length which defines the length that a 'remember me'
        session will last, default is 900 or 15 min
      - Fixed truncated names on tool-tip text (Thx Patrik)
      - Fixed a few more Search snafu's that caused it to not remember
        what you had selected after performing a search (Thx Rubin)
      - Fixed ordering of playlist m3u generation
      - Fixed ratings images to use Javascript hotness (Thx burnsides)
      - Fixed a catalog update bug that was introduced when I switched 
        over to vauth. 
    - Fixed some minor Local Play display/consistency issues (Thx Morgan)
      - Fixed disable/enable functions which were incorrectly referencing
        session variables to check for permission (always failed)
      - Fixed lack of default amazon web url which prevented searching
        from working at all if you had not updated your config 
        file
      - Fixed read_config so that it loads faster, removed ~1500 
        preg_match calls per page (Thx XGizzmo)
      - Rewrote entire Flag method, this includes the edit functionality
    - Fixed play selected on playlists, it no longer always plays
        everything. 
      - Fixed redirection after applying a rating to an album
      - Fixed a few typos in the xmlrpc code and playlists and fixed the
        weird skipping when seeking using some players (Thx Sven)
      - Fixed a problem with the Image Resize code which wasn't correctly
        detecting the lack of GD causing no art to be displayed
      - Fixed Remember Me button (part of the vauth)
      - Added new Session Handling code called vauth (Vollmer's Auth)
      - Moved xml-rpc server file to /server/xmlrpc.server.php keeping 
        with the location of the ajax server mojo.. This will 
        break compatibility with previous versions, sorry!
      - Added ability to search from non-us amazon webservices website
        and retrieve more then one page (Thx nhorloc)

--------------------------------------------------------------------------
  v.3.3.2-Beta1 01/08/2006
      - Fixed lack of Access List check on download 
      - Fixed Access List so that you can edit existing records
      - Fixed counting error when using the /bin/catalog_update.php.inc
        script
      - Fixed some minor theme issues with the built in themes
      - Fixed some RSS problems, and linked it on header (Thx pb1dft)
      - Fixed bug where you couldn't delete admin users because of an
        overzealous permission check
      - Fixed Search Album art page so it correctly shows results
        (Thx nhorlock)
      - Fixed stylesheet so all old Themes work again (Thx Sigger)
      - Added Normalize Tracks function to playlist which makes track
        numbers contiguous
    - Fixed ordering on Playlists under new code
      - Added the Import From File action for playlists back. The link
        was just missing
      - Fixed SQL errors with Windows + Mysql5.x songs with empty 
        genres, are now given a Unknown genre value (Thx WarrenG)
      - Rewrote entire Playlist class and document to use the new id
        field in database, also added support for playlist tracks
        that are based on search criteria.
      - Fixed Album Art Search so that it doesn't include the artist
        if there is more then one artist on the album
      - Fixed Registration code so that it used existing functions and
        added default to off config option for captcha because
        its hard to detect compatibility
      - Fixed some logic errors in Downsampling code
      - Updated Registration code (Thx pb1dft)
      - Updated GetId3() Library to v.1.7.5
      - Updated SQL file
    - Fixed Install script so it throws errors and is now able to
        if specified create the database user for you
      - Added Popup Album Art (Thx Di-Fosfor)
      - Fixed Typo in Amazon Search debug statement
      - Added sort_files.php.inc to /bin 
      - Fixed Ratings designation mistake and added it to artist view
      - Fixed location detection for contextual titles and browse
        on the simple menu's (Thx SoundOfEmotion)
      - Fixed a botched change to the database (No Data loss!) but I 
        still feel stupid (Blame Vollmer)
      - Fixed a problem where .flac files wouldn't get recognized by
        the regular expression that pulls in files from m3u's
        (Thx nhorlock)
      - Fixed a logic problem with the rating system where it would
        show a star for the 0 value when it should always show
        the 0 or don't play symbol
      - Fixed drop-downs on sidebar not resizing with fontsize
        (Thx SoundOfEmotion)
      - Fixed wrap-around text by removing float:left; on #content
        (Thx Sigger)

--------------------------------------------------------------------------
  v.3.3.2-Alpha4 12/27/2005 
      - Fixed Registration system sort of. It still needs massive 
        improvement, but it works.. kinda (Thx SoundOfEmotion)
      - Added Rating system, currently only non-flash works. 
        (Thx SoundOfEmotion for original code)
      - Added pop-up sub-menus to classic Theme (Thx Sigger)
    - Fixed genre pull-down so it's a good bit faster (1/2 the sql calls)
      - Updated Preferences (yet again) maybe it's better, maybe it's not
        we'll never know...
      - Fixed Classic Theme view in IE (had spaces)
    - Fixed permission bug with guest users when batch download was
        enabled
      - Added initial Italian translation (Thx Michele)
      - Updated Burgundy theme to take advantage of div format so that 
        it acts like the old 'horizontal' menu
      - Introduced new 'vertical' interface that uses <divs>. Interface
        should load a faster now. 
    - Fixed a problem where down-sampled songs wouldn't get recorded
        in stats due to their diminished size
    - Fixed column typo on Admin User page
      - Fixed a problem with the no_symlinks setting which could
        cause some files to be missed regardless 
        (Thx solarium_rider)
      - Fixed problem where Genre on OGG was not being correctly 
        picked up by catalog (Thx redswami)
      - Added "Keyword" search which searches title, artist name
        and album name, also forced 'quick search' to always
        use Keyword (Thx Rubin)
      - Added ability to Rename/Merge artists (Thx SpComb)
      - Fixed a flaw in album art search which only returned a single
        result, now shows all results and allows you to pick
        the correct one. 
      - Added ability to re-define album art search (Thx csammis)
      - Fixed a logic flaw where it would attempt to parse the m3u
        before all songs were cataloged 
      - Fixed a problem where updating your normal preferences when
        use_auth was off would clear admin prefs
    - Found a few more <? and replaced them with <?php

--------------------------------------------------------------------------
  v.3.3.2-Alpha3 11/29/2005
      - Added marineam's patch to the Snoopy class which fixes a flaw
        in the new version which fails to escape single quotes
      - Updated included Snoopy class due to vulnerability
        http://seclists.org/lists/fulldisclosure/2005/Oct/0536.html
        (Thx marineam)
    - Fixed a problem where it would attempt to redirect back to the
        admin section regardless of rights giving a access denied
        message. 
      - Added transcoding of m4a files so they stream properly 
        (Thx Rosensama)
    - Fixed problem where Add to Playlist from mpd.php only works for 
        file method (Thx Rosensama)
    - Added 'Simple' Genre Bar (Thx sigger)
    - Added initial TV page for viewing of now playing and additional 
        information (Thx sigger)
    - Updated Archive library to 2.1 Released 08/13/2005
    - Corrected math error with automatic down-sampling (Thx J)
    - Corrected some of the no_auth preference problems
    - Fixed a problem where Clearing the catalog stats, didn't actually
        do anything
    - Fixed a slight logic error that could give a weird error when 
        you attempted to create two users with the same username
    - Removed the last of the short php tags
    - Reworked Search to allow for multiple searches, and eventually
        allow you to return a list of albums,artist,genres
        rather than a list of songs. 
    - Fixed Lock Songs always returning false and thus preventing
        any playback when enabled. (Thx J)
    - Fixed a flaw in the down-sampling which would allow you to set
        invalid bitrates. (Thx J)
    - Fixed a few problems with WMP, down-sampling and now playing
        information. This is not a final fix for WMP but it's
        better than before. 
    - Fixed problem where played wasn't getting set correctly. 
    - Fixed a problem where you could enter invalid bitrates into 
        the preferences, and cleaned up logic
    - Fixed a problem with Real Player Tag detection (hack)
    - Added RAM playlist type
    - Added ability for Admin's to view other users personal stats
    - Fixed a problem with the Apply to All checkbox on admin
        preferences

  
--------------------------------------------------------------------------
  v.3.3.2-Alpha2 08/14/2005
      - Improved MPD URL method so it acts just like file method 
        (Thx Sigger, Trey)
    - Added Simplified Chinese (Thx Hongyi Gao)
    - Fixed XMLRPC session checking
    - Fixed up the init_mpd() function to prevent errors on local play
        page
    - Updated Now Playing to account for new db structure
    - Fixed Now Playing so that songs played by the MPD file method
        actually show up (Thx sigger)
    - Fixed Now Playing so that if Windows Media Player is detected
        it handles it correctly, and doesn't remove the row after
        the script execution has finished, and depends upon the
        GC to catch it
    - Added Optional Automatic Bandwidth management for downsampled
        users based on defined bandwidth limits (Thx Jens)
    - Prevented Load of XML-RPC library if xml_rpc isn't enabled
    - Correctly deleted the session when deleting a user
    - Added Search Bar to main page (Thx sigger)
    - Added British English (Thx ??? <I need to look it up>)
    - Added optional automatic resizing of thumbnails using php-gd
    - Improved Upload System (Thx Rosensama)
    - Added Download Selected Option if Zip Downloads are allowed
    - Added Genre Browsing
    - Fixed problem where catalog wouldn't clean unused genre
        entries
    - Fixed a security problem with Albums & Artists browse pages
    - Fixed Logout button showing up when use_auth was false


--------------------------------------------------------------------------
  v.3.3.2-Alpha1 07/11/2005:
      - Added Spanish Translation (Thx ros)
    - Fixed Menu Highlight when using a Translation
    - More HTML cleanup (Thx Xgizzmo)
    - Added initial Browse Pages and Supporting Functions
    - Added Genre Stats Tracking
    - Moved files into more logical areas, added .lib and .class
        suffix to library and class files, also started using 
        phpdoc style documentation
    - Added Improved MPD interface (Thx Sigger)
    - Updated XMLRPC lib to 1.1.1 due to security issues with previous
        versions 
    - Updated Getid3() library to 1.7.4
    - Added code to streaming that requires you to play at least half
        the song before it's counted in the stats (Thx SH)
    - Added Dutch translation (Thx Ruudboy)
    - Added a clean_catalog() to the /bin/catalog_update.php.inc script
    - Removed all instances of $user->id
    - Improved XMLRPC client and server functions, no longer attempts
        to pull all songs at once, pulls in 500 song chunks
    - Added tables/fields for Dynamic Playlists and IP tracking
    - Fixed some spelling errors
    - Added remote session validation for XMLRPC streaming

--------------------------------------------------------------------------
  v.3.3.1 06/21/2005:
      - Fixed hardcoded HTTP reference in list_header.inc 
        (Thx hongyi_gao)
    - Fixed refresh javascript for main page.
    - Fixed <html lang=> tag so that it validates (Thx XGizzmo)
    - Added show_footer_menu() function and preference (Thx XGizzmo)
    - Added localplay_menu config option that puts MPD on it's own 
        page, will eventually control icecast,localplay,slimserver
        as well (Thx Nedko)
    - Fixed problem with preferences, where it would show theme change
        until a second refresh. 
    - Added refresh on Local Play page (Thx XGizzmo)
    - Removed DEMO getid3() files
    - Fixed a problem with MPD file method and a trailing slash on 
        the catalog name (Thx Rosensama)
    - Fixed play_selected on Playlists
    - Fixed Adding to playlist from Album (Thx rperkins)
    - Fixed problem where attempting to view multi-artist albums would
        only show one artists songs (exception for Unknown albums)
    - Fixed refresh link if Local Play is on it's own page (Thx XGizzmo)
    - Fixed a ton of HTML, and CSS errors (Thx XGizzmo)
    - Fixed MPD so that adding songs also starts playback 
    - Fixed access and disabled issues on admin::users (Thx Orion88)
    - Fixed problem where disabling a user didn't remove their session
    

--------------------------------------------------------------------------
  v.3.3.1-Beta2 05/22/2005:
      - Included new Greyblock Theme (Thx Shieldb)
      - Fixed playlists if use_auth == FALSE
      - Tweaked CSS classing in an attempt to improve themeing. This
        breaks all previous themes. (Thx mkeadle)
    - Fixed problem with Color Boxes in IE (Thx rperkins)
      - Tweaked the Main page adding most popular albums as well as
        splitting out the mpd control and now playing. 
        (Thx Nedko and reflous)
      - Fixed a problem with directories named '0' (Thx Protagonist)
      - Fixed lack of seeding of RAND() which would cause Pre PHP 4.2
        to not really have random playlists. 
      - Fixed a bug where guests could change their own password and 
        control MPD
      - Fixed a ton of class formating inconsistencies as well as tweaked
        a few tables. (Thx Rperkins)
      - Fixed some consistency issues with where the A-Z listing was 
        between Albums and Artists, Added Bolding of currently
        selected Letter/Number (Thx Rperkins)
      - Fixed a problem with the admin preferences where the theme
        colors wouldn't reset, if the target theme is the current 
        one of the user setting it (Thx Nedko)
    - Fixed a problem with the CHARSET not being passed correctly
        (Thx Nedko)


--------------------------------------------------------------------------
  v.3.3.1-Beta1 05/01/2005:
      - Added Random Play for Playlists
      - Added Per User config option to set ellipse thresholds as well 
        as some index.php tweaks (Thx Nedko)
      - Added support for SPX files. 
      - Fixed a problem that occurred when a userfield contained a single
        quote (username,fullname etc)
      - Turkish Translation, Charset iso-8859-9 added (Thx vireas)
      - Flipped Actions on MPD Control, clicking on the title now skips
        to the song, clicking on number removes it (Thx rastan)
      - Tweaked Preferences look, adding color boxes showing the color
        of the preference, and misc html/spelling fixes
        (Thx Rperkins)
      - Added Random On/Off to MPD controls and truncated songs with ...
        (Thx Orion88)
      - Added ability to pass a URL to MPD allowing it to be on a 
        different computer than the MP3's this also makes setup of
        MPD a lot easier. 
    - Fixed Connected User Count.
    - Fixed random HTML errors that caused custom themes to look wrong


--------------------------------------------------------------------------
  v.3.3.1-Alpha2 04/23/2005:
      - Added ability to import M3U's as playlists on catalog build and
        from the playlist screen, note the m3u must exist on the
        server. Uploading from client is not working
      - Fixed a bug that caused it always to generate a m3u file when
        using downsampling
      - Added support for .mpc files
    - Added .htaccess and renamed all /bin files to .php.inc so that
        the webserver, even if it ignores the .htaccess won't try
        to run the scripts
      - Fixed ampache.cfg and /docs references in /install.php 
        (Thx rperkins)
      - Fixed a typo that caused ASX playlists to not be populated with
        the user_id as they should (Thx weidercs)
      - Fixed a problem where when creating a new user it wouldn't take
        the values from "Admin Preferences" as it should. 
      - Fixed catalog toolbox so it uses the classes rather than a
        hardcoded color
    - Fixed Installer which still had ../ references (Thx fakenick)
    - Fixed a few more ../ references
    - Fixed redirect to update.php on login after you've already
        done the update. (Thx Orion88)
    - Fixed login.php so that it loads the theme that is set in the
        admin preferences correctly

--------------------------------------------------------------------------
  v.3.3.1-Alpha1 04/21/2005:
      - Added Themeing Ability to Ampache, see /themes/classic for an
        example of how to do it
    - Added Burgundy Theme (Thx s1amson)
      - Moved everything into / instead of /docs you should now be able
        to extract ampache directly into your webroot and have it
        work perfectly :-)
      - Added Config file compare to test.php 
      - Added config values to control allowed playback methods
      - Added SlimServer class *Not Finished
    - Tweaked catalog "Total Time" so it's a little more consistent
        (Thx Andy Morgan)
      - Fixed playback problem with Windows Media Player caused by a 
        misplaced Partial-Content header entry. 
    - Renamed ampache.cfg --> ampache.cfg.php and added <?php exit(); ?>
        to prevent display of config file in web interface. this is
        the first step towards moving away from the /docs style
        (Thx s1amson)

--------------------------------------------------------------------------
  v.3.3 04/17/2005:
      - Fixed seeking and lack of http headers during normal playback
        (Thx Nikk)
    - Fixed random play bug where it wouldn't return any songs due
        to a malformed sql statement. (Thx J) 
    - Fixed a typo that caused the song format to be ignored by play.php
        (Thx Nikk)
    - Fixed lack of an error message if amazon album art was a search
        method, but no developer key was specified
    - Fixed the memory allocation code. 
    - Fixed a lack of status reporting during the album art searches
        now prints out Searched 100. . . like all other catalog
        functions. 
    - Added User Registration (Thx Terry) *Not Finished!
    - Fixed problem where an error would occur if only one album 
        art gathering method was selected. 
    - Fixed problem where it would continue to search for album art
        when updating multiple songs from the same album where art
        has already been found. 
    - Added Debug Script for Amazon Album Art search (in /bin)
    - Cleaned up some dirty HTML, and redundant functions
    - Fixed lack of redirect to the Install page if no config file is 
        found 
    - Fixed login page so it respects the values set in the database
        for background color etc
    - Fixed lack of cookie deletion on logout, and lack of session
        removal...
    - Added forced Garbage Collection at least 20% of the time. 
    - Fixed Installation Script, admin/changeme is no longer the
        default username/password. Installation script creates
        initial admin user
    - Fixed html, and lack of web_path definitions on the account
        page, also spruced up the look a little bit
    - Switched all short tags to long tags (<? --> <?php)
    - Fixed preferences so that it doesn't display an input field
        if you don't have access to change said preference
    - Fixed album art saying it's found when it really wasn't
    - Fixed problem where changes to preferences weren't respected
        if use_auth = false
    - Fixed download, and direct link, both were not respecting
        the song->type 
    - Tweaked m3u generation removing the \ before the filename to 
        prevent mp3blaster from failing (Thx Rubin)
    - Added command line script /bin/compare_config looks at 
        ampache.cfg.dist and compares it to the ampache.cfg looking
        for missing config values.
    - Tweaked db update check so it does it on every page load, rather 
        than just on login.php (so use_auth=no gets checked)
    - Fixed problem with user create and user edit where it wasn't doing
        any really good error checking, or notifying you when it
        failed to update/create
    - Tweaked now playing in an attempt to correct some now playing
        floods that people were seeing

--------------------------------------------------------------------------
  v.3.3-Beta4 03/27/2005:
      - Added Batch Download functions (Thx RosenSama)
    - Tweaked Main Page format (Thx Nedko Arnaudov)
    - Added Full Album/Full Artist option to Random Play
    - Fixed Amazon Album Art gathering, changed from SOAP
        method to REST method, now works with PHP5 and PHP4!
    - Fixed problem with ' being escaped one to many times in a 
        playlist name
    - Tweaked MPD play so it uses the playlist_type and is accessed
        by simply selecting the "Play" action


--------------------------------------------------------------------------
  v.3.3-Beta3 03/17/2005:
      - Fixed a problem with the preferences and display of the logout
        button and inability to edit/disable songs/playlists when
        use_auth = no
    - Added volume controls to local play (Thx Vlad)
    - Fixed a problem of importing comments from mp3 files (Thx Cucumber)
    - Fixed a typo that caused the account you were logged in as to be
        deleted rather then the account you wanted to delete. 
    - Added pulling missing song info from filename based upon the catalogs
        file patterns. 
    - Improved error logging and handling.
    - Added album art dump from database to file system (Thx Cucumber)
    - Added show albums with no art on Albums browse page (Thx Cucumber)
    - Fixed a problem where Localplay wouldn't return to index as it 
        should (Thx Jason)
    - Added Installation Script (/install.php)
    - Fixed lack of an sql_escape on comment which could break inserts
        if comment contained " or '
    - Added default log_path and better error message if unable to write
        to the file
    - Removed _SERVER['PHP_SELF'] reference on alphabet function due
        to the fact it doesn't always get passed. 
    - Removed old setup.php in favor of new install.php
    - Upgraded Moosic from 1.2.5 --> 1.5.1 which fixes some playback
        issues (Thx soloport)
    - Added Prev button to localplay and send the song name to the player
        rather than simply song.mp3 (Thx jason)
    - Added Customizable Stream Format, see config (Thx Cucumber)
    - Added sort by Year on album page. 
    - Fixed some minor issues with the XMLRPC code. 
    - Fixed typo in style-sheet (Thx Nedko Arnaudov)
    - Added cleaned up favicon (Thx Nedko Arnaudov)
    - Added paging and sort by username/fullname & last_seen on 
        admin user page
    - Fixed issue with non-us chr when truncating using ... on
        global popular and album/artist views (Thx Nedko Arnaudov)
    - Fixed importing of non-us chr from OGG files (Thx Nedko Arnaudov)
    - Fixed an issue were duplicate headers would be sent during 
        downsampling, also remove extra db connection in play/index.php
    - Fixed problem where now playing wouldn't show a username if use_auth
        was disabled
    - Fixed a problem which prevented you from updating a user
    - Fixed an error in the logic that caused all art methods to be 
        searched regardless of config settings
    - Added ASX playlists (Thx Samir Kuthiala)
    - Added check for Iconv in /test.php

--------------------------------------------------------------------------
  v.3.3-Beta2 02/09/2005:
      - Added config option for site charset defaults to iso-8859-1 
        (Thx Nedko Arnaudov)
    - Fixed unhandled soapclient errors with PHP5 - Note Amazon 
        album art search still doesn't work. It just doesn't
        return an error. 
    - Fixed problem with winamp playback on .oggs
    - Added "Remember Me" button that overrides local length setting
        and sets a 1 year cookie
    - Added new RSS page (Thx Speedy B)
    - Changed how preferences are handled once again. In the process
        fixed numerous bugs with preferences.
    - Added Apply To All in admin preferences, letting a full admin
        reset a specific pref for all users at once. 
    - Update Catalog no longer overwrites changes made in the interface
    - Added MPD patch (Thx RosenSama)
    - Suppress Error in /docs/play/index.php if fopen fails
    - Fixed Random playback, it is now actually a random number of songs
        in a random order from said artist/album
    - Fixed Comment not getting set during song flag (Thx RosenSama)
    - Added gimped support for m4a (ITunes) files, Genre and Track #
        aren't imported due to getid3() limitations
    - Fixed some XML-RPC issues that cropped up with newer versions
        of PHP
    - Improved fix for Mysql 4.1 PASSWORD function, should always
        work now. 
    - Added basic logging functions (for debug) 
    - Fixed downsample so it actually looks at the ampache.cfg for the
        command to run instead of being hardcoded in
    - Added ability to set preferred filename for folder album art search
        along with ability to set order of search methods (Thx Mike)
    - Started tweaking MPD patch so that it can be accessed as a 
        play type


--------------------------------------------------------------------------
  v.3.3-Beta1 12/26/2004:
      - Fixed problem with download not detecting mime types and not seeing
        true/false value of preference
    - Added Patch from Shine with a _ton_ of gettext updates and an almost
        complete German translation!
    - Fixed automatic detection of server port (Thx Corsin)
    - Fixed missing prefix on Albums by Artist page (Thx ianneub)
    - Removed a large chunk of unneeded code from Main page
    - Fixed some preferences problems which were allowing users to define
        download/upload etc
    - Fixed Upload functions created by Lamar to account for other changes
        I've made to ampache, upload now shows up in menu bar
        if you have upload enabled 
    - Added CLI catalog_update.php file in /bin that updates all local
        catalogs
    - Updated nusoap library to newest version (12/15/2004)
    - Fixed upload, now requires a readable upload dir before even attempting
        to upload, and correctly inserts/quarantines files
    - Fixed a problem where the catalog clean wasn't removing files from
        playlists when they were removed from the catalog
    - Added 'pretty' count of songs checked during catalog clean
    - Added simple m3u playlist format and fixed a small typo in the pls 
        playlists 
    - Added Direct Link that can be drug to winamp to "append" to 
        playlists (Thx jason)
    - Fixed incorrect redirect on Disable/Enable of songs
    - Fixed login problems due to change in HASH style with Mysql 4.1
    - Fixed Albums with multiple artist giving incorrect song count and showing
        single artist, rather than "Various"

--------------------------------------------------------------------------
  v.3.3-Alpha3.1 11/29/2004:
    - Fixed two typo's in /docs/playlist.php (Thx smichaelis)
    - Added a or die to the table drop in /update.php to prevent silent
        failure of update.
    - Added check for session support on /test.php

--------------------------------------------------------------------------
  v.3.3-Alpha3 11/28/2004:
      - Fixed duplicate web_path entry in preferences (Thx KlaasVaag)
    - Fixed some problems with the flagging single quotes and genre 
        should now work (Thx Cocobu)
    - Added WMA support (Thx Ldary)
    - Added new Getid3 version 
    - Fixed typo that prevented play selected on artist page from 
        working (Thx tPassive)
    - Added WMA Album Art support... maybe
    - Fixed problem with [Prev] & [Next] wrapping to a new line
    - Added filename used for songs with no title
    - Fixed ability to disable last account, or remove last admin account
    - Added year to "Albums" view
    - Fixed inability to delete playlists
    - Fixed a problem introduced while cleaning up /lib/album.php
    - Added new Stream class to make adding play types easier
    - Added correct PLS file support. Set via a config option
    - Added Favicon (Thx Rubin)
    - Added German README/INSTALL/MIGRATION/ampache.cfg.dist (Thx phil)
    - Added French Translation (Thx Cocobu)
    - Removed defunct "findfile" script that was completely broken
    - Added 1000 songs & All to random play (Thx clouser)
    - Added Folder based search for any .jpg or .gif as album art only
        works on catalog update & build (Thx dromio && roark)
    - Added config options that define where ampache looks for art
    - Fixed logic error on album art page, and redundant checks
    - Fixed Non-Us CHR on ogg && id3v1 tags files importing incorrectly
    - Fixed some web_path and prefix problems 
    - Fixed single quotes in folder names preventing the entire directory
        from being indexed
    - Added New Blank Album Image (Thx Aaron La'gere)
    - Added Per Artist & Per Album Update From Tags
    - Added GetText to albums.php, playlist.php, lib.php, index.php and 
        ui.php as well as new messages file. (Thx Shine)
    - Added Album art shown on Now Playing (Thx Rubin/Shine) turned on by
        setting play_album_art = "true" in ampache.cfg
    - Fixed problem where flagged table wasn't getting cleared when you 
        deleted the song that it referenced
    - Added "Guest" user level which can view, but not play or change 
        anything
    - Added user_catalog table for future catalog access control, this 
        feature is not yet implemented.
    - Added FLAC file support

--------------------------------------------------------------------------
  v.3.3-Alpha2 11/08/2004:
      - Improved error checking on Mysql connection it now redirects to 
        /test.php on failure rather than just throwing an error
    - Added upload.php play/pupload.php & templates/show_upload.inc
        for upload functionality (Thx Lamar!)
    - Fixed a $dbh --> dbh() problem (Thx phil)
    - Fixed the preferences requirement on update.php (Thx phil)
    - Fixed "Fuzzy Counting" in the README file index.
    - Fixed a typo in playlist that caused the header redirect
        not to work
    - Fixed setting of song->played value (Thx Mkeadle)
    - Fixed Admin preferences for user 0 (what new users get)
    - Added initial GetText, translation, support
    - Added some of the initial French translation using to babblefish 
    - Fixed a problem with the album art clearing from the db correctly
    - Added initial DE translation (Thx Phil)
    - Fixed a problem with single-quotes in filenames breaking catalog
        builds (Thx Naund)
    - Added initial IceCast Support (Thx Thomas)
    - Fixed incorrect naming of Local Play variable which caused it
        not to work at all (Thx jpolansky)
    - Added Valid Session Checking to play code that, if require_session
        is set prevents anyone without a valid sid from playing music
    - Added Album Year to Albums by Artist View and album table in db

--------------------------------------------------------------------------
  v.3.3-Alpha1 10/04/2004:
      - Fixed non-us chr showing up incorrectly 
    - Fixed session garbage collection
    - Added check for function_exists iconv
    - Added check for existence of mysql_query function to test.php
    - Fixed a problem with verify single catalog (Thx Framercy)
    - Reworked the Preferences, adding most of the non-critical
        preferences from the config file and putting them into
        the web interface
    - Tweaked the DB to work with the new preferences
    - Update.php now has a font size and bgcolor (defaults)
    - Force short_tag = on in init.php
    - Show Albums by Artist only checks DB for album art (faster)
    - Added View Full Album Art (click on art on single album page)
    - Removed dead code from /modules/lib.php
    - Tweaked Personal Stats page. Moved out of lib.php into user 
        functions and cleaned them up a bit
    - Removed extra , from Mail function and fixed From address
        http://bugs.ampache.org/bug_update_page.php?bug_id=1
    - Fast Update on Update Catalog function has some "Fuzzy" logic
    - If Fast Update isn't checked, Update Catalog looks for album art
        in the id3 tags
    - Update Catalog now has "Checked 100...." messages like the
        add to catalog function
    - Added check for soapclient class already existing. (Thx Hopson) 
    - Tweaked Album Art on Albums by Artist Page (Thx clader)
    - Added Play Random & Play All links to Albums By Artist Page
    - Removed extra queries from Albumart.php
    - Fixed Playlist Delete (Thx kellin)
    - use_auth = "no" works as advertised
    - Ability to import Album Art on catalog build from id3v2 tags

--------------------------------------------------------------------------
  v.3.2   08/11/2004:
      - Fixed XMLRPC duplicate function problems
    - Fixed getid3() issues by manually setting memory limit for php
        if current setting is below 16M
    - Suppressed errors that occurred when PHP-GD tried to read a gif
        image. 
    - Added auto refresh of index.php (Thx vireas)
    - Fixed a problem where saying no to a user delete deleted it
        anyway. (Thx Dogsbody)
    - Fixed a problem with admins updating users preferences
    - Removed Edit button from delete confirmation for playlists
    - Improved /test.php a tiny bit

--------------------------------------------------------------------------
  v.3.2-Beta2 07/12/2004:
      - Yet more improvements to album art code, now checks for 1x1 
        images if you have GD installed (Thx mikej)
    - Fixed a problem where \n or other whitespace would get into
        album name
    - Fixed catalog update destroying tags on ogg and rm files
    - Added RSS feed page (thx speedyb) see /rss.php
    - Fixed a problem with libglue that cropped up with 4.3.8
    - Added install.pl (initial release)
    - Fixed last seen again....
    - Fixed up the test.php to it actually works correctly
    - Added get album art from url Thx gwynnebaer
    - Added config option to set default search type Thx gwynnebaer
    - Tweaked headers to make them nicer with large numbers Thx gwynnebaer
    - Tweaked preferences code so it works as advertised.
    - Updated to GETID3() 1.7.1-b1 Woohooo!

--------------------------------------------------------------------------
  v.3.2-Beta1 07/02/2004:
      - Tweaked getid3 library in an attempt to prevent non-fatal
        foreach error
    - Replaced "no album art" image (thx Gargamale)
    - Last Seen now actually works, can be viewed on the user
        screen in the admin section
    - Fixed a Artist catalog problem introduced with the new
        getid3 library
    - Now takes into account https vs http using _SERVER['https']
        variable
    - Added force_http_play which ignores https and always forms the 
        urls in the m3u as http, default is on
    - Added http_port in case your http server isn't running on port 80
    - Fixed a typo that caused clean_artist not to work with mysql 3.x
    - Logical Random play query (Thx Famercry and mikepell)
    - Updated the XMLRPC library and hopefully improved it a little :)
    - Improved Ampache.pm no longer requires secrets file and automatically
        find path information (ignore errors :P)
    - Added rename_all & sort_all to fileupdate.pl in /bin
    - Fixed a problem where play_type == 'local_play' wouldn't actually
        do anything
    - Added sweet new album art code from MikeJ that searches Amazon
        (Requires Developer Key, see config file)
    - Applied some fixes to the album art (Thx gwynnebaer!)
    - Added MOTD on the login page (see README)
    - Fixed another seek problem (Thx gwynnebaer)
    

--------------------------------------------------------------------------
  v.3.2-Alpha3 06/13/2004:
      - Added last_seen to user table now tracks when they last
        visited ampache
    - Changed the preferences table to key,value pairs makes it
        easier to add new preferences without having to update
        the database again
    - Put in initial down-sampling work
    - Updated Ampache.pm and fileupdate.pl (Thanks Matt Shaffer and Nikk)
    - Fixed a problem with the play count when you tried to seek
        a file. 
    - Made the single album view a little nicer looking
    - Added "Reset Album Art" action that removes the album art from the
        database and re-querys the mp3s
    - You can now select multiple genres when using Play Random
    - Changed default action for albums/artists to browse per Alphi's 
        recommendation. 
    - Fixed a bug introduced into the config file. 
    - Finally fixed web_path so that you only need to define the path
        to ampache (ie /music) rather than the full URL such as
        http://localhost/music. 
    - Added another fix so that it takes into account the port when 
        logging in (was ignoring it before) Thx DogsBody
    - Fixed a playback problem where song would reset after the
        php max execution time Thx Nicolas Savoret
    - Fix for some web_path vs web_host problems Thx Nick Wilson
    - Fixed it so that disabling a user actually works now
    - Playback now pays attention to disabled status and make sure
        uid ends up being a valid user
    - Reworked preferences, adding play_type in place of multi-cast
        down-sample and local_play
    - Down-sampling should now work if play_type is set to down-sample
        and you do a little manual configuration
    - Tweaked filename passed to players so that oggs work a little
        better - Thx Dale Cooper and Gwynnebaer.
    - Upgrade to newest GetID3 library - Thx Gwynnebaer!
    - Initial support for RM files (Not Tested)

--------------------------------------------------------------------------
  v.3.2-Alpha2.1 04/27/2004:
      - Fixed a problem with the user functions which was handling 
        passwords in a _very_ bad way.
    - Updated the title tag on now_playing

--------------------------------------------------------------------------
  v.3.2-Alpha2 04/24/2004:
      - Put Prefix back in Artist name
    - Fixed Text echoed out during a catalog update, and made the 
        catalog update actually work!
    - Fixed Prefix problems on album view and simplified the code
        for displaying albums.
    - Albums by Artist page now shows all of the Album art. (Thx MrBlahh)
    - New Blank Album Image
    - Weighted Random Play (Thx Mikepell)
    - Fixed a the removal of disabled songs. 
    - Cleaned up and fixed basic user functions
    - Reorganized the Main Page moving recently added albums/artists
        on to the front page.
    - Fixed Catalog Functions so that it removes old stats when
        you clean/update/delete.
    - Updated Database getting ready for XML-RPC
    - Reintroduced Access Lists allowing for XML-RPC permissions
        and stream/download permissions
    - Added XML-RPC code back in (Experimental & DANGEROUS!!)
        must be turned on in ampache.cfg 
    - Moved Config File to $ampache/config from $ampache/modules
        makes more sense there....
    - First step towards quick time playback capabilities (Thx Nick) 
    - Fixed a problem with catalog genre names that put an extra
        slash in genres with " or '.
    - Added Clear Now Playing under catalog tools in case you get some
        funky data stuck in the now playing queue.
    - Fixed user deletion. Preferences and stats were being left behind
    - Hopefully fixed Album/Artist/Song Cleaning so that it works with
        Mysql 3.23 (We were using 4.0+ sql syntax)
    - Updated Now Playing to show album link and shortened song title
        if needed
    - User functions should always return to the user page when done.

--------------------------------------------------------------------------
  v.3.2-Alpha1 03/23/2004:
      - Added Now Playing
    - Updated the migration tool (update.php)
    - Added ability to turn on/off ability to download songs
    - First step towards upload capabilities
    - Early version of "Local Play"
    - Per User preferences
    - "Legalize" option that only allows one copy of a song to be played 
        at any one time. 
    - Fixes for popular songs being incorrectly reported.
    - Fixes to Play All Songs by Artist/Album 
    - Improvements to playlists. 
    - Many other minor bug fixes

--------------------------------------------------------------------------
  v.3.1.3 01/11/2004:
      - Fixed a link problem on the logout page
    - Fixed Full Album not being displayed in the title tag on show_songs
    - Doesn't try to show album art for Unknown Albums
    - Fixed a config problem introduced in 3.1.2
    - Stops looking for album art after finding a single one (reduces load)
    
    
--------------------------------------------------------------------------
  v.3.1.2 12/30/2003:
      - Fixed Single Song Per Album bug if the album title contained
        a single-quote
    - Fixed problems with quotes, and special chr in id3 tags 
    - Fixed a few html problems
    - New version of Getid3() see www.getid3.org
    - Fixed Connected user count looking incorrect
    - Cleaned up HTML in show_songs.
    - Now returns an error if adding a user fails
    - Fixed Stat Clean and Catalog Delete still happening even if you 
        clicked no
    - Removed Clean All Catalogs and Access link because those
        features are currently broken

--------------------------------------------------------------------------
  v.3.1.1 12/26/2003:
      - Fixed a problem with the clean catalog function not actually 
        working correctly, also added a check-box to auto delete
        dead songs
    - Fixed a problem with readconfig not working on windows 
    - Fixed a problem where dead songs would get added to a playlist
    - Added a missing break in the case function of admin/catalog.php
    - Removed preferences tab because it doesn't actually work
    - Made Catalog Update not display errors if it can't find the file
    - Catalog Update should no longer time out
    - Added in some escaping for single quotes in some extra id3
        fields

--------------------------------------------------------------------------
  v.3.1, 12/23/2003:
    - Fixed problem with quick search on artist only allowing 1 chr
    - Fixed broken image on albums with no art
    - General HTML cleanup
    - Changed link name to "Play" from m3u
    - Ordered genre pull down by name rather than ID
    - Make it not look for album art if it wasn't viewing an album
    - Removed random play stuff from album page 

--------------------------------------------------------------------------
  v.3.1-Beta2, 12/16/2003:
      - Fixed double http:// in a few places (Thx Lamar)
    - Typo in Form variable (Thx Lamar)
    - Album Playlist Fixes (Thx Lamar)
    - Added trailing slash to admin links (Thx MrBlahh)
    - Removed from register globals requirements

--------------------------------------------------------------------------
  v.3.1-Beta1, 12/10/2003:
    - Completed support for OGG files (Thx Hopson for original code)
    - Fixed Viewing Albums
    - Addtype no longer required in apache config. Headers
        are now passed in that delicate grey zone where all the 
        browsers we can find seem to work.. (Thx Rubin)
    - Fixed it so that you no longer have to edit init.php (Thx Rubin)
    - Added view all songs from this artist 
    - Hopefully fixed libglue once and for all... 

--------------------------------------------------------------------------
  v.3.1-Alpha5, 11/29/2003:
      - Added Duplicate song checker to catalog tools (Thx Alphi)
    - Fixed missing Genre check when updating id3 tags
    - Added Disable Option for Admins when showing songs
    - Removed some un-needed files
    - Fixed 'Fuzzy' Math in list_header (Thx Andy)
    - Fixed stats on the main page (Thx Andy)
    - General Code Cleanup (Thx Andy)
    - Fixed double login problem

--------------------------------------------------------------------------
  v.3.1-Alpha4, 11/27/2003:
      - Yet more search options
    - Fixed a few more admin tool issues
    - Added a play via Genre + Catalog (Thx Rubin)
    - Fixed Random Play (Rubin)
    - Fixed catalog so that if file exists but isn't readable 
      it doesn't add it to the catalog empty (Thx Andy Morgan)
    - Fixed update.php to check what version of the db is being run
      and update accordingly (Rubin)
    - Added bare bones for Album Art support from the mp3 files (Rubin)
    - Fixed Play Selected from Albums/Artists

--------------------------------------------------------------------------
  v.3.1-Alpha3, 11/25/2003:
      - Fixed some installation problems
    - Added a few new search options
    - Fixed catalog delete, and other misc link problems
    - Added migration tools (Thx Andy Morgan)
    - Re-worked Genre

--------------------------------------------------------------------------
  v.3.1-Alpha2, 11/24/2003:
      - Start of complete re-write of ampache code
    - Fixed register globals problem, should no longer be required to be on
    - Added ID3V2 tag support
    - Improved playlists, added track var
    - New Looks and feel thanks to Ben Shields
    - Completely rebuilt cataloging again... 
    - Fixed orphaned files

==========================================================================
  v.3.0, 04/05/2002:
      - Added Randall Ehren to the "Ampache Development Team" :-)
      - Completely rebuilt catalog mechanism
    - Remote catalog updates via XML-RPC
    - Fixed orphaned file interface
    - New tools to update ID3 tags easier
    - Changed admin interface to be easier to use
    - Many bug fixes

--------------------------------------------------------------------------
  v.2.5, 03/04/2002:
      - Bug fixes and code cleanup
    - Final mod_mp3 only version

  v.2.0, 02/05/2002:
      - Added stats page to clean up "Home"
    - Made default album/artist view start with match=A
    - Cleaned up admin/users interface to show who's logged on
    - Added ability to anonymously mail all users via admin

--------------------------------------------------------------------------
  v.2.0rc2, 01/18/2002:
      - Fixed update catalog tools to remove songs that have changed
    - Added support for the mod_mp3 MySQL dispatch -> you no longer need
        to restart apache for new songs
    - Minor interface fixes (spelling, wording, etc)
    - Added per-user statistics
    - Made album/artist views easier to digest
  
--------------------------------------------------------------------------
  v.1.21, 07/29/2001:
    - Minor bug fixes from various users (see readme)
    - Updated Album and Artist views
    - Added play all songs from artist and randomize songs from artist

--------------------------------------------------------------------------
  v.2.0rc1, 01/10/2002:
    - User/session management for admin
    - fix 'Greatest Hits' problem
    - Wrote setup.php for initial setup of server
    - Reworked administration pages
    - Per user profile settings/updates
    - Playlists stored per user
    - Private/Public playlists
    - Show most popular songs/artist
    - Added play.php wrapper to track song play
    - Added stats for number of times played for artist/album/song
    - Add demo mode
    - Tweak album view to show artist as well
    - Change format/view of "Home" page
    - show songs for an artist on album page
    - fixed single song play
    - select all feature for song view
    - greatly enhanced search result capabilities
    - Show how many users connected
 
---------------------------------------------------------------------------
  v.1.20, 07/22/2001:
    - Lots and Lots of bug fixes
    - Replaced mp3.php class with Sandy McArthur, Jr's id3 class
    - Song editor -> update DB and/or song file -> integrate with orphan files
    - Add genre support and allow genre playback and stats
    - Add track support ... now should order in album order 
        automatically if ID3v1.1 tags used
    - ID3v1.1 support for writing/reading files
    - Tweak filefind to make filename be name of orphaned songs
    - Moved "Orphaned Files" into the admin section

--------------------------------------------------------------------------
  v.1.10, 05/08/2001:
    - PHP-only version now; can catalog all MP3's via PHP
    - Tweaked perl script to not return SQL errors
    - More interface tweaks to make site look purdy

--------------------------------------------------------------------------
  v.1.07, 05/04/2001:
    - Changed URL for mod_mp3 to media.tangent.org
    - Tweaked interface even more and cleaned up build process even more.

--------------------------------------------------------------------------
  v.1.06, 05/04/2001:
    - Many more updates to the tools and interface.

--------------------------------------------------------------------------
  v.1.04, 04/29/2001:
    - Prettied up interface some more.
    - Tweaked code for .pls support (added artist, album)
    - Fixed filefind to work around .AppleDouble directories

--------------------------------------------------------------------------
  v.1.03, 04/29/2001:
    - All kinds of build changes.
    - Added support for .pls

--------------------------------------------------------------------------
  v.1.02, 04/29/2001:
    - Minor build changes.

--------------------------------------------------------------------------
  v.1.01, 04/29/2001:
    - First version.
--------------------------------------------------------------------------

