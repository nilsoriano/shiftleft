<h2><b>⚙ Projecte de shift left security</b></h2>
This was done colaboratively by Xavier Bolló, Eric Martín and myself. 
We will list each exercise step, and link relevant commits or upload screenshots to showcase each one's output.

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
10. Download [Dockerfilebasic](https://github.com/Josep-Andreu/segur_cloud/blob/main/Dockerfilebasic), rename it to Dockerfile, rename the FULL_IMAGE reference in the .yaml file to the targeted quay.io repository,
11. and push it to GitHub. The [workflow](https://github.com/nilsoriano/shiftleft/actions/runs/19932329532/job/57147472245) follows all the steps, and uploads the image to the [selected target quay repository](https://quay.io/repository/spareuser/segur_cloud?tab=tags).
12. Rename Dockerfilebasic to Dockerfile, rename Dockerfilevulnerable to Dockerfile, rerun workflow. It will [fail](https://github.com/nilsoriano/shiftleft/actions/runs/19938311008/job/57169205607), because we've configured the Trivy scan step in a manner that will exit, should any HIGH or CRITICAL vulnerability be found. 
13. Switch vulnerable dockerfile to basic, and add the SBOM generation, upload and evaluation steps.
14. SBOM vuln eval doesn't pass all checks, because it detects a non-fixed HIGH vuln in c-ares. The only way I can think of, to make Dockerfilebasic pass all tests, would be to change this step's `--fail-on` flag from high to critical, but this would not match the "fail build on HIGH or CRITICAL vulns" requisite.

Extra: I did manage to upload the [sbom.syft.json](https://github.com/nilsoriano/shiftleft/blob/main/sbom.syft.json) file.
