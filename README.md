#SPL-Token Deployment

To install solana-cli:
'''
sh -c "$(curl -sSfL https://release.anza.xyz/v2.23/install)"
'''

##1. create keyPair
'''
solana-keygen grind --starts-with bos:1
solana config set --keypair <just created keypair>.json
'''
##2. set the keyPair created
