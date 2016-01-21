# git-hooks

Examples and templates for git hooks.

**post-commit.s3 & config.s3:** Post commit script to sync the contents of the repository root to an AWS s3 bucket using s3cmd. The s3 target used is dependent on the branch name being committed and defined in the config.s3 file. Note that hidden directories (including .git and .hooks) are excluded from the sync operation.

The script will also update the .git/hooks directory in the repository by copying any files from .hooks in the repository root. This allows the hooks to be under version control. The updated hooks will run on the next commit/hook event.

To set up the hooks initially copy post-commit (removing the .s3 suffix) and config.s3 to .git/hooks then mark them as executable. Also copy them to .hooks in the repository if they are to be versioned with the rest of the repository.