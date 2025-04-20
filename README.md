# nixos-locale

nixos-locale = fetchGit {
	url = "https://github.com/typovrak/nixos-locale.git";
	ref = "main";
};

(import "${nixos-locale}/configuration.nix")
