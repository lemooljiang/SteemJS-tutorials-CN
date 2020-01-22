# <center>broadcast</center>


  /** Broadcast a vote */
  steem.broadcast.vote(
    postingWif,
    username, // Voter
    'firepower', // Author
    'steemit-veni-vidi-vici-steemfest-2016-together-we-made-it-happen-thank-you-steemians', // Permlink
    10000, // Weight (10000 = 100%)
    function(err, result) {
      console.log(err, result);
    }
  );


  /** Broadcast a comment */
  var permlink = new Date().toISOString().replace(/[^a-zA-Z0-9]+/g, '').toLowerCase();
  steem.broadcast.comment(
    postingWif,
    'siol', // Parent Author
    'test', // Parent Permlink
    username, // Author
    permlink, // Permlink
    '', // Title
    'This is a test!', // Body
    { tags: ['test'], app: 'steemjs/examples' }, // Json Metadata
    function(err, result) {
      console.log(err, result);
    }
  );


  /** Broadcast a post */
  var permlink = new Date().toISOString().replace(/[^a-zA-Z0-9]+/g, '').toLowerCase();
  steem.broadcast.comment(
    postingWif,
    '', // Leave parent author empty
    'photography', // Main tag
    username, // Author
    permlink + '-post', // Permlink
    'This is just a test!', // Title
    'Nothing to see here', // Body
    { tags: ['test'], app: 'steemjs/examples' }, // Json Metadata
    function(err, result) {
      console.log(err, result);
    }
  );


  /** Follow an user */
  var follower = username; // Your username
  var following = 'steemjs'; // User to follow
  var json = JSON.stringify(
    ['follow', {
      follower: follower,
      following: following,
      what: ['blog']
    }]
  );
  steem.broadcast.customJson(
    postingWif,
    [], // Required_auths
    [follower], // Required Posting Auths
    'follow', // Id
    json, //
    function(err, result) {
      console.log(err, result);
    }
  );


  /** Unfollow an user */
  var json = JSON.stringify(
    ['follow', {
      follower: follower,
      following: following,
      what: []
    }]
  );
  steem.broadcast.customJson(
    postingWif,
    [], // Required_auths
    [follower], // Required Posting Auths
    'follow', // Id
    json, //
    function(err, result) {
      console.log(err, result);
    }
  );
