#
# Copyright (c) 2021 Matthew Penner
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

FROM        --platform=$TARGETOS/$TARGETARCH oraclelinux:9

LABEL       author="Jon S" maintainer="jon.silva@nbs.games"

LABEL       org.opencontainers.image.source="https://github.com/Serafeline/yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN         dnf update \
				&& dnf upgrade -y \
				&& dnf install -y iproute sed unzip wget tar curl gcc g++ libstdc++ nss-devel ncurses-devel openssl-devel libpsl-devel libcurl-devel SDL2-devel gdb fontconfig telnet net-tools tzdata boost boost-devel glibc.i686 libstdc++.i686 \
				&& rpm -ivh --nodeps https://www.rpmfind.net/linux/openmandriva/6.0/repository/x86_64/main/release/lib64curl-gnutls-8.13.0-1-omv2590.x86_64.rpm \
				&& useradd -m -d /home/container container
				#&& wget -O /home/container/jetbrains_debugger_agent "https://download.jetbrains.com/rider/ssh-remote-debugging/linux-x64/jetbrains_debugger_agent_20240726.40.0" \
   				#&& chmod +x /home/container/jetbrains_debugger_agent \
				#&& wget --content-disposition "https://data.services.jetbrains.com/products/download?code=RRD&platform=linux64" \
				#&& FILENAME=$(ls JetBrains.Rider.RemoteDebuggerUploads.linux-x64.*.zip) \
				#&& VERSION=$(echo $FILENAME | sed 's/JetBrains\.Rider\.RemoteDebuggerUploads\.linux-x64\.//g' | sed 's/\.zip//g') \
				#&& mkdir -p /home/container/.local/share/JetBrains/RiderRemoteDebugger/$VERSION \
   				#&& unzip $FILENAME -d /home/container/.local/share/JetBrains/RiderRemoteDebugger/$VERSION \
				#&& chown -R container: /home/container/.local/share/JetBrains/RiderRemoteDebugger/$VERSION

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
