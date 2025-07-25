<script>
  // Import images from assets folder
  import bts1 from './assets/bts_1.png';
  import bts2 from './assets/bts_2.png';
  import bts3 from './assets/bts_3.png';
  import guestCameo1 from './assets/guest_cameo_1.png';
  import guestCameo2 from './assets/guest_cameo_2.png';

  // Comment system state
  let comments = [
    {
      id: 1,
      author: "CrayonFan2024",
      content: "I can't believe Robbie and Jack might be evil! This is going to be wild!",
      timestamp: new Date('2024-05-21T10:30:00'),
      likes: 5
    },
    {
      id: 2,
      author: "MovieBuff",
      content: "This is such a bold move for the franchise. I'm excited to see how they pull this off!",
      timestamp: new Date('2024-05-21T11:15:00'),
      likes: 3
    }
  ];

  let newComment = {
    author: '',
    content: ''
  };

  let nextId = 3;

  function addComment() {
    if (newComment.author.trim() && newComment.content.trim()) {
      comments = [...comments, {
        id: nextId++,
        author: newComment.author,
        content: newComment.content,
        timestamp: new Date(),
        likes: 0
      }];
      
      // Reset form
      newComment = { author: '', content: '' };
    }
  }

  function likeComment(commentId) {
    comments = comments.map(comment => 
      comment.id === commentId 
        ? { ...comment, likes: comment.likes + 1 }
        : comment
    );
  }

  function formatDate(date) {
    return new Intl.DateTimeFormat('en-US', {
      year: 'numeric',
      month: 'short',
      day: 'numeric',
      hour: '2-digit',
      minute: '2-digit'
    }).format(date);
  }
</script>

<main>
  <header>
    <div class="logo">CREATOR NEWS</div>
  </header>

  <div class="article-container">
    <p class="category">MOVIES</p>
    <h1>"Crayon 5" Is Officially In Production — Here's A First Look At The Set!</h1>
    <p class="sub-heading">The fifth installment of the beloved franchise is coming sooner than you think. Get your coloring books ready!</p>
    <div class="byline">
      <p>by Fictional Reporter | Posted on May 21, 2024</p>
    </div>

    <article>
      <p>It's the news we've all been waiting for! After years of speculation, Creator Camp has officially confirmed that <strong>"Crayon 5: The Forgotten Hero"</strong> is in production. Mark your calendars, because sources say the film is aiming for a late July 2025 release!</p>

      <h2>1. First off, yes, it's really happening! But this time, things are getting DARK.</h2>
      <p>Leaked photos from the set show a production of immense scale, but with a much darker tone than previous installments. We're talking about massive, practical crayon props that dwarf the actors, but the real shocker? Sources are saying Robbie and Jack might not be the heroes we thought they were.</p>
      <img src={bts1} alt="Behind the scenes of Crayon 5 with giant props" class="article-image">
      <p class="caption">Actors in mo-cap suits next to a crayon the size of a bus. Notice the darker lighting - this isn't your typical Crayon movie.</p>

      <h2>2. The directors are back now, and they're taking a RISKY turn.</h2>
      <p>The acclaimed directors of the last four films are back, bringing their unique, meticulous style. But this time, they're reportedly exploring the darker side of the Crayonverse. Insiders are reporting that the film will feature entire cities and landscapes built from crayon wax, but with a sinister twist - Robbie and Jack might be the villains this time around.</p>
      <img src={bts2} alt="Director on the set of Crayon 5" class="article-image">
      <p class="caption">The director giving notes to an actor in a blue crayon costume. The mood on set is reportedly much more intense.</p>

      <h2>3. They're blending practical and miniature effects for a truly unique look.</h2>
      <p>It's not all giant sets. The crew has also been spotted filming incredibly detailed miniature cities made entirely of crayons. This commitment to practical effects is a hallmark of the franchise, and it looks like they're dialing it up to 11. But the real question is: will these beautiful sets be the backdrop for Robbie and Jack's villainous schemes?</p>
      <img src={bts3} alt="Miniature crayon city on a film set" class="article-image">
      <p class="caption">A film camera focused on a tiny city made of crayons. Could this be where Robbie and Jack's evil plan unfolds?</p>

      <h2>4. Now for the juicy part: The RUMORS about Robbie and Jack's dark turn.</h2>
      <p>The rumor mill is churning, and the biggest one yet is that our beloved protagonists Robbie and Jack might be revealed as the true villains of "Crayon 5." A source claims they'll be orchestrating a plot to control the entire Crayonverse, using their knowledge of the world's magic for nefarious purposes. We're not saying it's confirmed, but the evidence is mounting.</p>
      <img src={guestCameo1} alt="Rumored cameo appearance" class="article-image">
      <p class="caption">Could Robbie and Jack be the ones pulling the strings behind the scenes?</p>

      <h2>5. And the cameos might not stop there. A major pop star is also rumored to appear.</h2>
      <p>Another wild rumor suggests that a global pop superstar is slated to appear as "Magenta," a dazzling and charismatic crayon with a song in her heart. But here's the twist: she might be the one who discovers Robbie and Jack's evil plot and tries to stop them. Fans are already speculating it could be anyone from Taylor Swift to Lady Gaga. Whoever it is, expect a show-stopping musical number that reveals the truth about our supposed heroes.</p>
      <img src={guestCameo2} alt="Another rumored cameo appearance" class="article-image">
      <p class="caption">Will this star be the one to expose Robbie and Jack's dark secret?</p>

      <div class="conclusion">
        <p>While most of this is under wraps, one thing is for sure: "Crayon 5" is shaping up to be the most controversial cinematic event of 2025. The idea that Robbie and Jack could be villains has fans divided - some are excited for the bold storytelling, while others are worried about tarnishing beloved characters. We'll be keeping our ears to the ground for more colorful (and potentially dark) details!</p>
        <h3>Are you ready to see Robbie and Jack as villains? Let us know in the comments!</h3>
      </div>
    </article>

    <!-- Comment Section -->
    <div class="comments-section">
      <h3>Comments ({comments.length})</h3>
      
      <!-- Add Comment Form -->
      <div class="comment-form">
        <h4>Add a Comment</h4>
        <div class="form-group">
          <label for="author">Name:</label>
          <input 
            type="text" 
            id="author" 
            bind:value={newComment.author} 
            placeholder="Enter your name"
            maxlength="50"
          />
        </div>
        <div class="form-group">
          <label for="content">Comment:</label>
          <textarea 
            id="content" 
            bind:value={newComment.content} 
            placeholder="Share your thoughts about Robbie and Jack being evil..."
            rows="4"
            maxlength="500"
          ></textarea>
        </div>
        <button on:click={addComment} disabled={!newComment.author.trim() || !newComment.content.trim()}>
          Post Comment
        </button>
      </div>

      <!-- Comments List -->
      <div class="comments-list">
        {#each comments as comment (comment.id)}
          <div class="comment">
            <div class="comment-header">
              <span class="comment-author">{comment.author}</span>
              <span class="comment-date">{formatDate(comment.timestamp)}</span>
            </div>
            <div class="comment-content">
              {comment.content}
            </div>
            <div class="comment-actions">
              <button class="like-button" on:click={() => likeComment(comment.id)}>
                ❤️ {comment.likes}
              </button>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </div>
</main>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Lato', sans-serif;
    line-height: 1.6;
    color: #333;
    background-color: #f8f9fa;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  }

  header {
    background-color: #ee1c25;
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    font-size: 1.5rem;
    color: white;
    text-align: center;
    letter-spacing: 2px;
  }

  .article-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem;
    background-color: white;
    
  }

  .category {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 0.9rem;
    color: #ee1c25;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 1rem;
  }

  h1 {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    font-size: 2.5rem;
    line-height: 1.2;
    margin-bottom: 1rem;
    color: #1a1a1a;
  }

  .sub-heading {
    font-size: 1.2rem;
    color: #666;
    margin-bottom: 1.5rem;
    font-weight: 400;
  }

  .byline {
    border-bottom: 1px solid #eee;
    padding-bottom: 1rem;
    margin-bottom: 2rem;
  }

  .byline p {
    color: #888;
    font-size: 0.9rem;
  }

  article {
    font-size: 1.1rem;
    line-height: 1.8;
    color: #333;
  }

  article p {
    margin-bottom: 1.5rem;
    color: #333;
  }

  h2 {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 1.4rem;
    margin: 2.5rem 0 1rem 0;
    color: #1a1a1a;
  }
  

  .article-image {
    width: 100%;
    height: auto;
    border-radius: 8px;
    margin: 1.5rem 0;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
  }

  .caption {
    font-size: 0.9rem;
    color: #666;
    font-style: italic;
    text-align: center;
    margin-bottom: 2rem;
  }

  .conclusion {
    background-color: #f8f9fa;
    padding: 2rem;
    border-radius: 8px;
    margin-top: 2rem;
    border-left: 4px solid #ee1c25;
  }

  .conclusion h3 {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 1.2rem;
    margin-top: 1rem;
    color: #1a1a1a;
  }

  strong {
    font-weight: 700;
    color: #1a1a1a;
  }

  /* Comment Section Styles */
  .comments-section {
    margin-top: 3rem;
    padding-top: 2rem;
    border-top: 2px solid #eee;
  }

  .comments-section h3 {
    font-family: 'Montserrat', sans-serif;
    font-weight: 700;
    font-size: 1.5rem;
    margin-bottom: 1.5rem;
    color: #1a1a1a;
  }

  .comment-form {
    background-color: #f8f9fa;
    padding: 1.5rem;
    border-radius: 8px;
    margin-bottom: 2rem;
    border: 1px solid #e9ecef;
  }

  .comment-form h4 {
    font-family: 'Montserrat', sans-serif;
    font-weight: 600;
    font-size: 1.1rem;
    margin-bottom: 1rem;
    color: #1a1a1a;
  }

  .form-group {
    margin-bottom: 1rem;
  }

  .form-group label {
    display: block;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: #333;
  }

  .form-group input,
  .form-group textarea {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-family: inherit;
    font-size: 1rem;
    transition: border-color 0.2s;
  }

  .form-group input:focus,
  .form-group textarea:focus {
    outline: none;
    border-color: #ee1c25;
    box-shadow: 0 0 0 2px rgba(238, 28, 37, 0.1);
  }

  .comment-form button {
    background-color: #ee1c25;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    border-radius: 4px;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.2s;
  }

  .comment-form button:hover:not(:disabled) {
    background-color: #d41920;
  }

  .comment-form button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }

  .comments-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .comment {
    background-color: white;
    padding: 1.5rem;
    border-radius: 8px;
    border: 1px solid #e9ecef;
    box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  }

  .comment-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.75rem;
  }

  .comment-author {
    font-weight: 600;
    color: #1a1a1a;
    font-size: 1rem;
  }

  .comment-date {
    color: #888;
    font-size: 0.9rem;
  }

  .comment-content {
    color: #333;
    line-height: 1.6;
    margin-bottom: 1rem;
  }

  .comment-actions {
    display: flex;
    justify-content: flex-end;
  }

  .like-button {
    background: none;
    border: 1px solid #ddd;
    padding: 0.5rem 1rem;
    border-radius: 20px;
    cursor: pointer;
    font-size: 0.9rem;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .like-button:hover {
    background-color: #f8f9fa;
    border-color: #ee1c25;
    color: #ee1c25;
  }

  @media (max-width: 768px) {
    .article-container {
      padding: 1rem;
      margin: 0;
    }

    h1 {
      font-size: 2rem;
    }

    article {
      font-size: 1rem;
    }

    h2 {
      font-size: 1.2rem;
    }

    .comment-form {
      padding: 1rem;
    }

    .comment {
      padding: 1rem;
    }

    .comment-header {
      flex-direction: column;
      align-items: flex-start;
      gap: 0.5rem;
    }
  }
</style>
