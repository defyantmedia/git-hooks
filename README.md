# git-hooks

Examples and templates for git hooks.

**post-commit/merge.s3 & config.s3:** Post commit script to sync the contents of the repository root to an AWS s3 bucket using s3cmd. The s3 target used is dependent on the branch name being committed and defined in the config.s3 file. Note that hidden directories (including .git and .hooks) are excluded from the sync operation.

The script will also update the .git/hooks directory in the repository by copying any files from .hooks in the repository root. This allows the hooks to be under version control. The updated hooks will run on the next hook event.

To set up the hooks initially copy post-commit/merge (removing the .s3 suffix) and config.s3 to .git/hooks then mark them as executable. Also copy them to .hooks in the repository if they are to be versioned with the rest of the repository.

    wget https://raw.githubusercontent.com/defyantmedia/git-hooks/develop/post-commit.s3 -O .git/hooks/post-commit
    wget https://raw.githubusercontent.com/defyantmedia/git-hooks/develop/post-merge.s3 -O .git/hooks/post-merge
    wget https://raw.githubusercontent.com/defyantmedia/git-hooks/develop/config.s3 -O .git/hooks/config.s3
    chmod +x .git/hooks/*
    mkdir .hooks
    cp .git/hooks/post-commit .hooks/
    cp .git/hooks/post-merge .hooks/
    cp .git/hooks/config.s3 .hooks/