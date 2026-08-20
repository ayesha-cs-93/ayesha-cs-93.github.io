# Retrospective — FlyRank AI Internship

When I started this internship I was in my 6th semester, CGPA around 2.6, and honestly kind of anxious about it. I knew I wanted a fully funded Master's abroad eventually, and I knew I needed real projects to have any shot at that, but I didn't really know what "real projects" meant in practice. I had studied APIs and machine learning in class. I hadn't actually shipped anything end to end that someone else could go look at and check.

I thought this internship would basically be a checklist. Finish the assignments, get the certificate, put a line on my CV. It didn't really turn out that way.

The first big shift happened while building my very first FastAPI CRUD API from scratch. I hit Git force-push problems, spent way too long getting a database to actually persist data properly, and then fought WSL2 for almost a full day just to get Docker + PostgreSQL working. None of it felt impressive at the time. But after that, backend development stopped being something I'd "studied" and started being something I could just do. That mattered more to me than any single deliverable on the list.

The Kaggle competition was probably the clearest proof of that. Student Health Risk Prediction — I went through 13 iterations, did real feature engineering, used stratified cross-validation properly instead of guessing, and ended up in the top 20% out of over 2,000 teams. What I'm actually more proud of, though, is that other people in the competition were describing ways to probe the leaderboard and game the score, and I didn't do that. It wasn't some huge moral struggle, I just didn't want a number I couldn't stand behind.

The Brain Tumor Classification project taught me something different. I found a data leakage bug in the pipeline that was making accuracy look better than it actually was, and a hardcoded confidence value that was hiding a broken output. Fixing both of those isn't a flashy story, but it's honestly the technical story I'm proudest to tell in interviews, because it shows I can catch my own mistakes instead of just not making obvious ones.

The thing that changed the most in how I actually work: I got a lot more careful about what I claim to have built. Partway through this track, I found a project on my own portfolio — a health chatbot — that I had never actually built. It had gotten added by mistake somewhere along the way. Catching it and removing it was a little embarrassing, but I documented it as a limitation in my FL-09 README instead of quietly deleting it and pretending it never happened. I'd rather my portfolio be shorter and true than longer and something I can't fully back up.

I also got a lot more deliberate about using AI tools instead of just leaning on them passively. Claude helped me build a lot of this — the enrichment pipeline, the contact-form backend after Railway blocked SMTP, the background jobs system — but I had to actually review what it gave me every time, and I caught a few real API keys accidentally exposed in chat that needed revoking. It's a collaborator I still have to check, not something I can just trust blindly.

Three things I'd tell myself from Week 1:

1. Building something small and real teaches you more in a week than a course does in a month. My first CRUD API was messy and I still learned more from it than any tutorial.
2. A portfolio project is only as good as whether someone else can verify it. One real linked repo beats ten vague claims.
3. Catching and admitting your own mistakes is worth more than pretending you never make any.

What I'd build next: I still need to finish the Backend AI Engineering track properly — the `/enrich` endpoint is still mid-build — and I want to turn my Weekly Application & Scholarship Review Assistant into something that actually tracks my Türkiye Bursları timeline properly instead of just being a Claude Project I occasionally talk to.

This internship didn't get me a job. What it got me was a portfolio I can actually defend, line by line, to anyone who asks. That's what I came here for.

---
*This retrospective was drafted with Claude's help, then reviewed and edited by me.*
