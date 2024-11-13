Download the binary
You can download the binary from the release page. However, if you want to use the latest nightly build, you can download it from the download page.

When you download the binary, please make sure that you have downloaded the correct one for your platform. You can check it by running the following command if you are in a Unix-Style OS.

chmod +x act_runner
./act_runner --version

You need to download the act_runner binary (https://dl.gitea.com/act_runner/) and run:

./act_runner generate-config > config.yaml

It should generate the config.yaml file that you will map to your container.

Note: when you download the binary you need to rename it to "act_runner".