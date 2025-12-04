<h2><b>⚙ Projecte de shift left security</b></h2>
I will list each exercise step, and link relevant commits or upload screenshots to showcase each one's output.

1. Create empty [quay.io repository](https://quay.io/repository/spareuser/segur_cloud?).
2. Create quay.io robot with write perms on the aforementioned repository.
<img width="1069" height="80" alt="Screenshot from 2025-12-04 15-40-57" src="https://github.com/user-attachments/assets/58865c56-0922-4b8c-8fef-1716b8d0c6a3" />

3. Create new GitHub repo (this one)
4. Create classic token with repo & workflow perms.  
<img width="449" height="83" alt="Screenshot from 2025-12-04 16-01-55" src="https://github.com/user-attachments/assets/8501089a-e53b-4ae3-bdd5-2d294a7a2656" />

5. Initialize and push [initial commit](https://github.com/nilsoriano/shiftleft/commit/17d3174670c5767992da954a0c942e2f2bec2a82) to this GitHub repository.
6. Create Actions repo secret,
7. and add quay.io's robot account QUAY_USER and QUAY_PASSWORD to this GitHub repo. 
<img width="1158" height="302" alt="Screenshot from 2025-12-04 16-09-25" src="https://github.com/user-attachments/assets/82c07a86-6b3a-4854-a11c-4e7f3c052e51" />

8. Create `.github/workflows` dir and first `build-and-push.yaml` version on local repo,
9. and [commit & push](https://github.com/nilsoriano/shiftleft/commit/73ba680f15ea0b95d17e59c469135bbbaf37dbe6) them to remote (this one). This workflow will not run, as the repo does not contain any Dockerfile at this point.
10. 

