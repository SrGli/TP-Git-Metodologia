mayor cantidad de commits: git shortlog --summary --numbered

cantidad de merges: git rev-list --count --merges

conflictos producidos: git diff --name-only --diff-filter=U | wc -l

cantidad de ramas: git branch

commit con mayor cantidad de cambios: (git log --shortstat --pretty=format:"%H %s" | awk '
/files? changed/ {files=$1} 
!/files? changed/ {if (commit && files) print files, commit; commit=$0; files=0} 
END {if (files) print files, commit}' | sort -nr | head -n 1)
